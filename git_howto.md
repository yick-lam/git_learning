# This docuemtn is obsoleted.  It is moved to other personal server

This is just some not very organized note for git.

- Check out 
    - In svn,  
      svn co svn://yylam.XXX.org/trunk/Examples/git
    - In git,   
      clone https://github.com/yick-lam/EngDict_MS_Pinyin.git 

- To update the branch:
    - cd EngDict_MS_Pinyin
    - git pull origin main   
      origin: meaning the original repository (github)  
      main: meaning the branch name, github use main

- Suppose you modify eng_dict.txt
    - use `git diff` to produce "patch" style difference
    - setup of `gitdiff` script:
        - set default difftool to vimdiff  
          `git config --global diff.tool vimdiff`
        - turn off the annoying "Launch tool [Y/n]?" prompt  
          `git config --global difftool.prompt false`
        - Add alias to `~/.bashrc` for your old muscle‑memory   
          `alias gitdiff='git difftool'`
        - Reload shell:  
          `source ~/.bashrc`
    - use `git status` to show what is changed

    - Preparatory steps to commit changes locally and to the server:
        - `git config --global user.name "Yick Lam"`
        - `git config --global user.email "yick.lam@gmail.com"`
        - `git config --global core.editor "vi"`  
          this is to configure to use vi
        - do the ssh procedures in svn://.../trunk/Examples/ssh:
            - `cp id_rsa id_rsa.pub ~/.ssh`
            - `chmod 600 ~/.ssh/id_rsa`
            - `cat ~/.ssh/id_rsa.pub` and copy the content 
            - goto github.com > Accessbility > SSH and GPG
            - ADD new SSH Key
                - Title: ylam-RSA
                - Key type: Autentication
                - Key: ssh-rsa ......
            - `ssh -T git@github.com`  
              Test if OK.
            - `git remote set-url origin git@github.com:yick-lam/EngDict_MS_Pinyin.git`  
              switch your local repo from HTTPS to SSH

    - to commit and push the change:
        - `git add eng_chi_dict.txt`  
          add the change to the staging area
        - `git commit` 
          commit the change to the repository in the editor  
          `git commit -a` can be used without staging area
        - `git push origin main`  
          push the change to the remote repository

    - to check the log:
        - git log
        - gitdiff 5248277971b0f0ce7 1fed06eb2ab32
        - gitdiff HEAD '@{2.days.ago}'
        - gitdiff HEAD~2 HEAD~1
        - git log --oneline

- How to add a new repository:
    - mkdir ~/git_learning
    - cd ~/git_learning
    - git init -b main
    - git add README.md
    - 
    

