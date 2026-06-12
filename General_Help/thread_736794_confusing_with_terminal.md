---
title: "confusing with terminal"
date: 2008-03-27
forum: General Help
---

### Post by chathurangamdk on 2008-03-27
I 'm using Ubuntu Gusty Gibbon 7.10. When I open a terminal on my desktop few of lines are printing automatically. These are the lines,.....

bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: not: no completion specification
bash: complete: included: no completion specification
bash: complete: in: no completion specification
bash: complete: the: no completion specification
bash: complete: PATH: no completion specification
bash: complete: environment: no completion specification
bash: complete: variable.: no completion specification
mdkc@icta-desktop:~$ 



After that when I type an usual commands like "ls", it gives this message ,

mdkc@icta-desktop:~$ ls
Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
bash: ls: command not found
mdkc@icta-desktop:~$ 

Please help me to fix this problem.
Thank You!

---

### Post by -grubby on 2008-03-27
Could you please post your .bashrc (in /home/user/.bashrc)

---

### Post by chathurangamdk on 2008-03-27
This was inside /etc/bash.bashrc. There's no bashrc file in /home/user/. 

# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
	function command_not_found_handle {
                /usr/bin/python /usr/lib/command-not-found -- $1
                return $?
	}
fi
export JAVA_HOME=/home/icta/jdk1.6.0
export PATH=$JAVA_HOME/bin:$PATH
export PATH=$HOME/eclipse

---

