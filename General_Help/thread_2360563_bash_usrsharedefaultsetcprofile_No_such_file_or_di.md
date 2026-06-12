---
title: "bash: /usr/share/defaults/etc/profile: No such file or directory"
date: 2017-05-05
forum: General Help
---

### Post by chase-gooding on 2017-05-05
I recently upgraded to Ubuntu 17.04. My install ended up getting messed up. After several attempts at other options, I ended up reinstalling Ubuntu from scratch. However, before I reinstalled, I created a new partition and copied all of the /home files to it.  My intent was to have a separate /home partition so that in case an install/upgrade ever fails in the future, it won't wipe my person files, settings, etc.  When I did this, I think I had the wrong permissions for the files so that only root could change them.  I have since changed that so that my user has permission.  But, as a result of that issue, I believe the install failed to setup the "profile" files.

I used this thread to create the .profile file in my user folder: [https://askubuntu.com/questions/652822/bash-home-rathin-profile-no-such-file-or-directory-while-trying-to-reload-i](https://askubuntu.com/questions/652822/bash-home-rathin-profile-no-such-file-or-directory-while-trying-to-reload-i)

However, now I am receiving the error as seen in the title: bash: /usr/share/defaults/etc/profile: No such file or directory

What should be in this "profile" file? TIA

---

### Post by ajgreeny on 2017-05-06
I don't have such a file either in my Xubuntu 16.04, but I do, of course have a .profile in my home which contains
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

export GTK_OVERLAY_SCROLLING=0
gdbus call --session --dest org.freedesktop.DBus --object-path /org/freedesktop/DBus --method org.freedesktop.DBus.UpdateActivationEnvironment '{"GTK_OVERLAY_SCROLLING": "0"}'


```

---

### Post by steeldriver on 2017-05-06
Can you explain exactly how you used the information in the askubuntu post that you linked? I don't see /usr/share/defaults mentioned anywhere on that page

FYI the default user .profile file is copied from /etc/skel/.profile on account creation - so if you want to revert you can always do

```

mv ~/.profile ~/.profile.old

cp /etc/skel/.profile ~/

```

---

### Post by efflandt on 2017-05-06
Note that **.profile** is a hidden file that begins with a dot.
/etc/skel/ contains the default files that go into a user's directory if you use: **sudo adduser** *username*
The flip side "useradd" does not add a home directory (used for daemons, etc.)

---

### Post by oldos2er on 2017-05-06
There is an /etc/profile, which contains ```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

```

---

### Post by chase-gooding on 2017-05-06
> **oldos2er said:**
> There is an /etc/profile, which contains ```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

```

My /etc/profile is also identical to that.

> **steeldriver said:**
> Can you explain exactly how you used the information in the askubuntu post that you linked? I don't see /usr/share/defaults mentioned anywhere on that page

FYI the default user .profile file is copied from /etc/skel/.profile on account creation - so if you want to revert you can always do

```

mv ~/.profile ~/.profile.old

cp /etc/skel/.profile ~/

```

I looked at all of my .profiles and such. /etc/skel/.profile is identical to the ~/.profile. To follow the askubuntu thread, I followed the code comment from "Terrance" on 7/26/2015 beginning with "In the meantime...". I, of course, replace "rathin" with my username "chase".

I think I also failed to mention that this ierror is the first line when I open Terminal.  My terminal is not auto-completing commands like "sudo apt-g<tab> upd<tab>". So I think the problem has something to do with the error message.

---

### Post by steeldriver on 2017-05-06
Can you share your ~/.bashrc as well? or at least

```

diff -s /etc/skel/.bashrc ~/.bashrc

```

Also please check whether you have a `~/.bash_profile`

---

### Post by chase-gooding on 2017-05-07
I think we've discovered the problem. The contents of ~/.bashrc is:

```
source /usr/share/defaults/etc/profile


```

However, the contents of /etc/skel/.bashrc is:

```
# ~/.bashrc: executed by bash(1) for non-login shells.# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples


# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac


# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth


# append to the history file, don't overwrite it
shopt -s histappend


# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000


# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar


# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"


# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac


# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes


if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi


if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt


# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac


# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'


    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi


# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'


# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'


# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'


# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.


if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

So I will replace my ~/.bashrc with /etc/skel/.bashrc and see what happens.  Also, there is no ~/.bash_profile.

---

### Post by chase-gooding on 2017-05-07
Whelp...still getting the same issue.  Now I'm wondering if my /etc/bash.bashrc is correct.  Here are the contents currently:

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
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
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
#if ! shopt -oq posix; then
#  if [ -f /usr/share/bash-completion/bash_completion ]; then
#    . /usr/share/bash-completion/bash_completion
#  elif [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#  fi
#fi


# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *|*\ sudo\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi


# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/lib/command-not-found -- "$1"
                   return $?
                elif [ -x /usr/share/command-not-found/command-not-found ]; then
		   /usr/share/command-not-found/command-not-found -- "$1"
                   return $?
		else
		   printf "%s: command not found\n" "$1" >&2
		   return 127
		fi
	}
fi
```

---

### Post by steeldriver on 2017-05-07
Have you logged out and back in since replacing your ~/.bashrc with the one from /etc/skel?

Is the ~/.bashrc file getting modified with a non-default one again, or are you getting the same problem even with the correct (default) file?

---

### Post by chase-gooding on 2017-05-07
Looks like I concatenated ~/.bashrc instead of overwriting.  The first line was still "[COLOR=#000000][FONT=&quot]source /usr/share/defaults/etc/profile". I removed that and it's working now.[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-05-08
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

