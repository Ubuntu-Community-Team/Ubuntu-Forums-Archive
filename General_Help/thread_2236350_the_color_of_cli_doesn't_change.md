---
title: "the color of cli doesn't change"
date: 2014-07-26
forum: General Help
---

### Post by aviv2 on 2014-07-26
hi guys, i have followed this manual
[https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt)
i have tried to copy paste from other bashrc samples and the color stay the same when i ssh, why?

---

### Post by mcduck on 2014-07-26
can you give a bit more details? What type of terminal emulator are you using to connect through SSH? Have you enabled colors in that terminal, as well as on the bashrc of the user & computer you are connection to?

---

### Post by bulrush2 on 2014-07-26
OP, this all depends on how bash interprets the escape sequences. 

> if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi

What characters is .bashrc expecting? Is it expecting slash, zero, three, three, or do you have to use your editor's "enter special character" function to enter an actual escape character? 

I'm not familiar with bash, but for csh, to change the X window title, I had to enter an actual escape character. The escape ctr showed up in nedit, but NOT when I 'more' the csh script.

---

### Post by aviv2 on 2014-07-26
the emulator is putty, but it doesn't matter cause when i connect to kali, i see the colors of the cli, about what bashrc expecting?how can i know?
this is how its in my .bachrc file:



if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\$
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

---

### Post by sudodus on 2014-07-26
I think I learned how to get a nice prompt in a thread here at the Ubuntu Forums. Now it is my turn to help you. I have the following code in my ~/.bashrc file:

```

# set a fancy prompt (non-color, unless we know we "want" color)

# start BigglesPIP's colour prompt

if [ "$TERM" == "xterm" ]
then
 typeset TERM=xterm-color  # force colour prompt
fi

function statstring {
RC=$?
  if [ "0" != $RC ]; then
    printf "[$RC] "
  fi
}

case "$TERM" in
xterm-color)
#    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

    if [ "$USER" = root ]; then
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;31m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    else
        PS1='\[\033[01;31m\]$(statstring)\[\033[00m\]${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\] \[\033[01;34m\]\w\[\033[00m\] \$ '
    fi
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

if [ "$TERM" == "xterm-color" ]
then
 typeset TERM=xterm  # force basic prompt
fi

# end BigglesPIP's colour prompt

```

---

### Post by mcduck on 2014-07-26
> **aviv2 said:**
> the emulator is putty, but it doesn't matter cause when i connect to kali, i see the colors of the cli, about what bashrc expecting?how can i know?
this is how its in my .bachrc file:



if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\$
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

Do you actually have somewhere a line that sets $color_prompt to "yes"?

edit: Here's all the color-related stuff from my bashrc (which works fine both on my local system and on my remote server through SSH (from both my Ubuntu machine and from Windows machines using PuTTY):
```

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes

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

```

---

