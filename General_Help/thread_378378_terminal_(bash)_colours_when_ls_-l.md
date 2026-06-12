---
title: "terminal (bash) colours when ls -l"
date: 2007-03-07
forum: General Help
---

### Post by cope on 2007-03-07
Hi, 

I installed from the alternate cd since I have a ATI card that the live CD for some reason couldn't manage to find causing the X-install to crash.. What i've found though is the terminal isn't colourful. For example, I "ls -l" and the directories used to come through in different colours then the files, etc. etc... Can someone tell me what i'm doing wrong, heres a snippet from my .bashrc file! 

##edit##
I've uncommented and commented as per the instructions below, but it only changes my prompt (cope@desktop:~$) and not the ls output. 

```

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
    PROMPT_COMMAND='echo -ne "\033]0;${HOSTNAME}:\007"'
    ;;
*)
    ;;
esac

```

---

### Post by cope on 2007-03-07
damn i'm an idiot :)

alias ls='ls --color=tty'

sorry guys, its late down under

---

