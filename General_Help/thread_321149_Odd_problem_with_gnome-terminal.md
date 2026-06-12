---
title: "Odd problem with gnome-terminal"
date: 2006-12-18
forum: General Help
---

### Post by yopnono on 2006-12-18
Ok you know if using the terminal and you type something like ```
sud
``` then press the TAB button it finish the word, in this case it will type ```
sudo
```

But if I use the TAB function it works unless I use sudo in the begin of the line, then it don't do anything.


Example if using terminal and not using the word sudo then I can type ```
apti
``` and press TAB and it will finish it to ```
aptitude
``` Then I do the same except I only add sudo to the terminal it don't work any more. Like this ```
sudo apti
``` and press TAB button it don't finish the word aptitude.

**SOLVED**

---

### Post by hanzomon4 on 2006-12-18
I get this prblom every so often, never could figure out why

---

### Post by annda on 2006-12-18
what happens if you press TAB twice? sometimes there is more than one alternative - double TAB should list them all.

or type another letter or two and hit TAB again. that should help too.

---

### Post by Lord Illidan on 2006-12-18
Can you give us your ~/.bashrc ?

---

### Post by yopnono on 2006-12-18
> **annda said:**
> what happens if you press TAB twice? sometimes there is more than one alternative - double TAB should list them all.

or type another letter or two and hit TAB again. that should help too.

Nothing. But I did notice something right now, If I type sudo aptit and press ESC then press TAB it will finish of the aptitude, and next time I press TAB nothing. I need to press esc and then tab again.

---

### Post by hikaricore on 2006-12-18
I know I have this issue in edgy, usually I just type/tab the command I need then hit "home" to add sudo to the beginning of the line *shrug*

I don't remember if I had this issue in dapper or not.

---

### Post by yopnono on 2006-12-18
> **Lord Illidan said:**
> Can you give us your ~/.bashrc ?

Don't have any file called that. Have .bash_history

---

### Post by Lord Illidan on 2006-12-18
Strange, then your /etc/bash.bashrc

---

### Post by yopnono on 2006-12-18
> **Lord Illidan said:**
> Strange, then your /etc/bash.bashrc

```
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
```

Did create a .bashrc
```
# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi
```

Still the same.

---

### Post by yopnono on 2006-12-18
Solved I did create a new user then I took the bash files from the new user, and now it's working.  But why don't they get created if missing?

Attached them for others to use.

---

