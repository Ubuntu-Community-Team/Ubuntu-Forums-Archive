---
title: "Bash Completion"
date: 2008-04-22
forum: General Help
---

### Post by yochaigal on 2008-04-22
Hey ---

After Hardy RC Clean install, bash-completion wasn't installed. I've installed it, but it doesn't work with apt-get.
Example:
sudo apt-get install gno[tab to complete goes here]
should have finished with gnome.

Any ideas?  I've reinstalled the package, no-can-do.

---

### Post by elamericano on 2008-04-22
There are lots of packages that start with "gno". The next letter does not have to be 'm'. Does it give a list if you hit tab more than once?

---

### Post by yochaigal on 2008-04-22
that was just an example.
Anyways it does that with any package --- and i can run bash completion through apt-get on my other hardy machine (an eeepc).

And also, if it was working it would ask me to display all X number of packages, now it just beeps.

---

### Post by elamericano on 2008-04-22
Sorry, please provide actual examples. Is apt-get the only problem? Does ls tab-complete? Does sudo ls not work? It might be useful to know if sudo or apt-get is having the problem, or if it just doesn't work at all.

---

### Post by yochaigal on 2008-04-22
Tab completion works fine; But I cannot install anything without typing it in exactly as I remember it; for example:

sudo apt-get install gmounti[tab] 
does not yield anything;
while on my eeepc 
sudo apt-get install gmountiso appears

Does that make more sense?

See this thread: 
[http://ubuntuforums.org/showthread.php?t=702142](http://ubuntuforums.org/showthread.php?t=702142)

---

### Post by Joeb454 on 2008-04-22
I had the same issue. I believe an update solved it :)

Alternatively you could check your bash settings etc.

---

### Post by elamericano on 2008-04-22
If it's related to settings, the reinstall method should be "complete removal of bash-completion and/or bash, followed by a reinstall. Of course, if you have a custom .bashrc or color schemes, you'd need to save them.

I just tried this myself, and it didn't cause any problems.

---

### Post by elamericano on 2008-04-22
I was assuming Synaptic there, but you could also use:

sudo apt-get --purge remove bash-completion
sudo apt-get install bash-completion

---

### Post by yochaigal on 2008-04-22
Yeah I've already done all that... cleaned in and out.
No dice.

---

### Post by elamericano on 2008-04-22
OK, investigating how bash-completion works, I see it uses 

apt-cache pkgnames

to complete that command.

apt-cache pkgnames | grep gmounti

returns: gmountiso on my computer. What do you get?

---

### Post by yochaigal on 2008-04-22
I get the same return....
hmmm.
I have uninstalled and reinstalled it three times now, purged everything. 
Curious.

---

### Post by elamericano on 2008-04-22
On my system:

ls -l /etc/bash_completion

-rw-r--r-- 1 root root 216529 2008-04-14 18:45 /etc/bash_completion

If you can cat the file, then bash should have access. I suppose it's bash script debugging after that...

---

### Post by yochaigal on 2008-04-22
Output of :
ls -l /etc/bash_completion
-rw-r--r-- 1 root root 216529 2008-04-14 18:45 /etc/bash_completion

and I can cat the file, too.

Hmmm... 

Where is .bashrc found?

---

### Post by yochaigal on 2008-04-22
So I checked /etc/bash.bashrc and it looks pretty typical -


-----------------------------------------------------------------
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
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- $1
                   return $?
		else
		   return 127
		fi
	}
fi

----------------------------------------------------------------


Any ideas?

---

### Post by elamericano on 2008-04-22
That's identical to my /etc/bash.bashrc. I suppose we're both running version 3.2.33(1)-release.

~/.bashrc has a part at the end about completion:
```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups
# ... and ignore same sucessive entries.
export HISTCONTROL=ignoreboth

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ] && [ -x /usr/bin/dircolors ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

```
You could try moving that to the top, in case something in there is causing it to exit before the end.

---

### Post by elamericano on 2008-04-22
You can do it manually from the command line first to see if it might help:
```
. /etc/bash_completion
```
That's a dot and a space at the beginning.

---

### Post by yochaigal on 2008-04-22
Moving it to the beginning worked!!!

What could be causing it to fail? I wish there was some sort of logging/debugger output for it....

So it works now. 

Thanks a lot----

---

### Post by elamericano on 2008-04-22
I glad you stayed with it. I was losing hope.

You can add a line like "echo sofarsogood" to .bashrc and then run bash to see how far it's getting. You know, put it in the middle, then move halfway up or down depending on if it prints or not. You would definitely find the failing command that way.

---

### Post by elamericano on 2008-04-22
There's not much that can fail after you ignore the comments:

1. [ -z "$PS1" ] && return
2. shopt -s checkwinsize
3. [ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"
4. eval "`dircolors -b`"

That's about it.

---

