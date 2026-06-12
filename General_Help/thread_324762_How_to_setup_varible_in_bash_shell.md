---
title: "How to setup varible in bash shell"
date: 2006-12-24
forum: General Help
---

### Post by moonhk on 2006-12-24
Dear Reader

How to setup varible in bash shell ?

Step 1.edit .bash_profile, Add ksh=/home/moonh/shell
Step 2. Close terminal 
Step 3. Open Terminal again.
Step 4, echo $ksh , Return blank line



moonhk@HEX:~$ cat .bash_profile
# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

PATH=${PATH}:/home/moonhk/shell
ksh=/home/moonh/shell

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
moonhk@HEX:~$

#####################################
echo ksh value

moonhk@HEX:~$ echo ${ksh}

moonhk@HEX:~$

---

### Post by bodhi.zazen on 2006-12-24
bash_profile is not used for terminals, just at login.....

Put your variable in .bashrc

echo $ksh

---

### Post by moonhk on 2006-12-24
Thank. It works.

---

### Post by bodhi.zazen on 2006-12-24
You are most welcome ! 8)

---

