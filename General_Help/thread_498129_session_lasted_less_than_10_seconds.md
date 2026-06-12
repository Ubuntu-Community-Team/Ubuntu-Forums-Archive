---
title: "session lasted less than 10 seconds"
date: 2007-07-11
forum: General Help
---

### Post by sumanta on 2007-07-11
I have installed Ubunru 7.04. I had been running it smoothly for 10 or 15 days. But currently facing the same problem i.e., "session lasted less than 10 seconds". I tried so many things to get rid of things but failed .
Currently I am working in failsef gnome. Any help?
The .xsession-errors is giving the following errors:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "sumanta"
/etc/gdm/Xsession: Beginning session setup...
/etc/bash.bashrc: 11: shopt: not found
/etc/bash.bashrc: 54: Syntax error: "}" unexpected (expecting "fi")
__________________

---

### Post by tgalati4 on 2007-07-11
Obviously something is borked.  Try posting your .bashrc so we can take a look.

---

### Post by Espreon on 2007-07-11
Well, maybe try Googling your problem.
If all fails (after extensive modding) reinstall.

---

### Post by sumanta on 2007-07-12
Here is the bashrc file 

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
if [ -x /usr/bin/command-not-found ]; then
	function command_not_found_handle {
                /usr/bin/command-not-found $1
                return $?
	}
fi

---

