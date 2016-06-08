git doc.
工作区 --> 暂存区 --> 本地仓库 --> 远程仓库

一、基础操作
1、git init
//将该文件夹初始化为git 仓库

2、git status 
//检查当前文件状态

3、git add <path>
//将指定的文件或目录递归添加到暂存区, 可使用通配符

4、git commit [-m “comment”]
//提交到本地的仓库

5、git checkout <path>
//取消对指定文件的修改(返回暂存区)

6、git rm –cached
//当指定的文件从暂存区中删除

7、git log
// 显示提交的log 及 commit(SHA-1  40 char)

8、git difftool --cached			
//查看暂存区与仓库的文件内容差异

9、git difftool README.md                         
//查看README.md 工作区文件与暂存区中的差别

10、git difftool <commit>			
//查看工作区与指定commit的文件内容差异

11、git reset <commit>			
//重置为commit版本
	--soft						仓库置为<commit>, 工作区与暂存区不变
	--hard						工作区,暂存区,仓库置为<commit>

12、git config --global credential.helper cache     
//密码会放在内存中一段时间，可不必每次都输密码15分钟

二、远程
1、git remote add <nickname> <url>
//添加一个新的取名例如ruanzf的远程仓库

2、git fetch <nickname>
//添加完远程后，得先和远程同步

3、git push <nickname> <branch-name>
//git push ruanzf master
//本地commit后的master 分支推送到ruanzf这个刚添加的远程服务器上

三、分支
1、git checkout -b branch_1                        
//创建branch_1分支，并切换到该分支

2、git branch                                      
//查看本地分支

3、git ls-remote
//查看远程分支

4、git checkout master     
//本地分支切换到master

5、git rebase branch_1  或者  git merge branch_1             
//把branch_1分支中修改的内容合并到master分支

6、合并分支:

    branch_1 修改文件并commit（存入数据库）后才能被master分支合并
    master 必需把所有修改都commit后，才能合并branch_1分支的修改

    merge方法:切换至master分支(参考6)
    git merge branch_1
    1、没有冲突，合并成功
    2、产生冲突，打开冲突文件，合并冲突后，add、commit, 合并成功

    rebase方法:切换至master分支(参考6)
    git rebase branch_1
    1、没有冲突，合并成功
    2、产生冲突，会生一个新的带有冲突文件的临时分支，在该分支中打开冲突文件，合并冲突后，add、commit
    3、git rebase --continue 合并成功，临时分支被删除

7、git push origin branch_1    
//创建并推送到远程分支，要在branch_1分支下面

8、git checkout -b branch_1 origin/branch_1        
//假设本地没有branch_1分支，把远程branch_1分支拉下来并切换到该分支

9、git merge origin/master -m 'merge reason'     
//合并分支master到branch_1(原分支在branch_1)

10、git push origin branch_1        
//单独推送branch_1分支到远程


