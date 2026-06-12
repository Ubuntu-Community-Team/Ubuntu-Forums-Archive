---
title: "Java Install problems"
date: 2005-04-14
forum: General Help
---

### Post by FOF on 2005-04-14
Just a little problem.
After installing Open Office 2 Beta I tried to install J2SE Runtime Environment (JRE)?
by following the unofficial Ubuntu guide using copy and paste commands
It downloaded ok but when finished I ended up with the bash.bashrc file opening every time I run the root terminal - Gedit.
The file reads:

# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" -a -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
sudo chown -R root:root /usr/java/jre1.5.0_02/
sudo ln -s /usr/java/jre1.5.0_02/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_02/bin/java_vm /usr/bin/java_vm
sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
sudo gedit /etc/bash.bashrc
# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
    ;;
*)
    ;;
esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi
#JAVA_HOME=/usr/java/jre1.5.0_02
#export JAVA_HOME
#PATH=$PATH:$JAVA_HOME/bin
#export PATH
 
The bottom four lines I have commented out.

Can anyone throw some light on my mistakes...
Thanks in Advance
FOF

---

### Post by hagman on 2005-04-14
Hi,

Look at this part in your bashrc:

> 
sudo chown -R root:root /usr/java/jre1.5.0_02/
sudo ln -s /usr/java/jre1.5.0_02/bin/java /usr/bin/java
sudo ln -s /usr/java/jre1.5.0_02/bin/java_vm /usr/bin/java_vm
sudo cp /etc/bash.bashrc /etc/bash.bashrc_backup
sudo gedit /etc/bash.bashrc 

It might be a copy&paste error. These lines have to be executed in a terminal, not in your bashrc.

Cheers, 

Helge

---

### Post by FOF on 2005-04-14
Thanks.
I will take it out and see what happens
 FOF

---

### Post by FOF on 2005-04-14
Thanks Hagman,
Back to normal now.
I copied the Bash.bashrc_backup file and replaced bashrc.
Now to get java working.

Thanks again
FOF

---

### Post by artinla on 2005-04-14
Those last four lines that you commented out need to be uncommented.

Also, to test java functionality open a terminal and type:

java -version

if it responds with a version number,  java is working.


Art

---

### Post by FOF on 2005-04-14
Hello Art,
I tried the java - version 
got back 
bash: java: command not found
In open office it is showing there is a java on the system but not working.
Any thoughts on that ..

Thank you.
FOF

---

