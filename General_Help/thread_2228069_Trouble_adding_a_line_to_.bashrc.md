---
title: "Trouble adding a line to .bashrc"
date: 2014-06-05
forum: General Help
---

### Post by alexandra3 on 2014-06-05
I'm trying to install some software (EMAN2), but whenever I try, I get the message

"Please add the following line to the end of your /home/[username]/.bashrc:
source /home/[username]/Downloads/EMAN2/eman2.bashrc"

However, I have done that. I have tried it both using the echo command and editing .bashrc myself. The line is there, but for whatever reason, it keeps insisting that I need to add it. Can anyone help? (I'm pretty close to a beginner.)

---

### Post by papibe on 2014-06-05
Hi alexandra3. Welcome to the forum ):P

Could you post the content of your current ~/.bashrc?

If we can take a look, we may be able to make some suggestions.

Regards.

---

### Post by alexandra3 on 2014-06-05
I'm not sure if you need the comments as well, but I'll include them just in case. Here it is:

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
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
    xterm-color) color_prompt=yes;;
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

source /home/[username]/Downloads/EMAN3/eman2.bashrc
```

---

### Post by deadflowr on 2014-06-05
> source /home/[username]/Downloads/EMAN3/eman2.bashrc
change the entry to your username
```
source /home/yourusername/Downloads/EMAN3/eman2.bashrc
```
or simply use $HOME
```
$HOME/Downloads/EMAN3/eman2.bashrc
```
Hope that helps.

---

### Post by monkeybrain20122 on 2014-06-05
You need to logout and log back in for it to take effect.

---

### Post by alexandra3 on 2014-06-05
It doesn't literally say [username]. It has my username there, I just took it out because there's personal info in it.

---

### Post by papibe on 2014-06-05
> **alexandra3 said:**
> It doesn't literally say [username]. It has my username there, I just took it out because there's personal info in it.
Make sure the file is there:
```
ls /home/yourusername/Downloads/EMAN3/eman2.bashrc
```
Is it there?

Regards.

EDIT: may be it is a typo? EMAN3 shouldn't be EMAN**[COLOR="#FF0000"]2[/COLOR]** ?

---

### Post by alexandra3 on 2014-06-05
> [COLOR=#000000]EDIT: may be it is a typo? EMAN3 shouldn't be EMAN[/COLOR][B][COLOR=#FF0000]2[/COLOR] ?
[/B]
Oh, man, I'm going to feel so stupid if this was the only problem.

---

### Post by alexandra3 on 2014-06-05
I fixed the typo, but am still having the problem. I've already logged out and back in several times. And I checked, and the file was there.

---

### Post by steeldriver on 2014-06-05
is your shell something other than bash maybe (csh, ksh, zsh)?

---

### Post by monkeybrain20122 on 2014-06-05
Try to put the line in .profile instead of .bashrc then logout and login.

---

### Post by alexandra3 on 2014-06-05
My shell is bash. I tried adding the line to .profile and logging out and then in, but it dind't fix the problem.

---

### Post by steeldriver on 2014-06-05
What exactly is the command you're using that produces the message? 

Are you installing a binary package or building from source?

---

### Post by alexandra3 on 2014-06-05
The command is ./eman2-installer, and I'm installing a binary package.

---

### Post by papibe on 2014-06-05
If it is in ~/.bashrc, you don't have to logout, just open a new terminal, and work from there.

Did you check that the path is correct?

Could you open a terminal and run this command?
```
[[ -f /home/yourusername/Downloads/EMAN2/eman2.bashrc ]] && echo "path is correct."
```
(please replace 'yourusername' with your actual username).

Regards.

---

### Post by monkeybrain20122 on 2014-06-05
Well seems to work here. Maybe you have a space after the line you pasted? papibe is correct, no need to logout and login.

Seems like a cool program. :) BTW, you need to install python-qt4-gl for it to work, maybe other python-qt packages too if you have not had them already.

---

### Post by alexandra3 on 2014-06-06
papibe, I ran that command, and it said "path is correct."
monkeybrain, I installed python-qt4-gl, but I'm still getting the same message when I try to install it. I don't know why it's working for you but not for me. D: There's no space after the line I pasted, I checked.

---

### Post by monkeybrain20122 on 2014-06-06
Hmm... 
Did you run the install script with sudo (system wide)? 32 or 64 bits? 

Mine is just for me (no sudo ) and 64 bits.

Edited: python-qt4-gl has nothing to do with your problem, but you will encounter error when running the tests if it is not installed (after you get your issue sorted), so I just mentioned that as additional info.

---

### Post by alexandra3 on 2014-06-06
I ran it without sudo and 64 bits.

---

### Post by mc4man on 2014-06-06
Have you tried to use eman2 yet?
(maybe the only purpose of the installer script is to give you the proper line to add to your .bashrc, so re-running the installer script will just keep telling you the same thing

what's this say
```
echo $PATH
```

---

### Post by monkeybrain20122 on 2014-06-07
Well not sure if it would make a difference. But instead of extracting the tar file to Downloads, extract it to /home/yourusername and run the install script again. Of course remove the line you added to .bashrc first, also delete your old EMAN2 folder in Downloads.

---

### Post by mc4man on 2014-06-07
> **monkeybrain20122 said:**
> Well not sure if it would make a difference. But instead of extracting the tar file to Downloads, extract it to /home/yourusername and run the install script again. Of course remove the line you added to .bashrc first, also delete your old EMAN2 folder in Downloads.
Don't think it really matters.
I  went ahead & dl'ed this to see.
The installer does 2 things
Creates a eman2.bashrc file to set runtime environment using the paths discovered when the installer script is run
Gives you a source line to add to your .bash
That's it, the only reason to rerun the installer is if one moved the EMAN2 folder

---

### Post by alexandra3 on 2014-06-09
> **mc4man said:**
> Don't think it really matters.
I  went ahead & dl'ed this to see.
The installer does 2 things
Creates a eman2.bashrc file to set runtime environment using the paths discovered when the installer script is run
Gives you a source line to add to your .bash
That's it, the only reason to rerun the installer is if one moved the EMAN2 folder
Does that mean it should already be installed, or what?

---

### Post by mc4man on 2014-06-09
> **alexandra3 said:**
> Does that mean it should already be installed ..
As 'installed' as it's ever going to be. Refer back to post [here ]("http://ubuntuforums.org/showthread.php?t=2228069&p=13042346&viewfull=1#post13042346") for some info on running, -  ask here or somewhere on how to use the apt if you don't know how.

---

