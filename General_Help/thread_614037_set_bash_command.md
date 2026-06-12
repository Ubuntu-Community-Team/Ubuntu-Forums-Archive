---
title: "set bash command"
date: 2007-11-15
forum: General Help
---

### Post by dreadrea on 2007-11-15
when I execute set command without options from command line the output  display environment variables more "some code". Is it normal or it is an error?

---

### Post by jfinkels on 2007-11-15
[http://www.computerhope.com/unix/uset.htm](http://www.computerhope.com/unix/uset.htm)

---

### Post by bingoUV on 2007-11-15
what do you want to achieve by set command? 

It is not an error that you see. set shows all keywords, including functions that are defined in your environment.

---

### Post by dreadrea on 2007-11-15
Thanks for your reply. What I mean is that when I do "set"  in another distribution the output only display the value of environment variables like PATH or USER, but here there is some code before .there is not in others distributions.
This is some of the output:

OSTYPE=linux-gnu
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/
usr/games
PIPESTATUS=([0]="0")
PPID=6003
PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
PS2='> '
PS4='+ '
PWD=/home/carlosxabier
SESSION_MANAGER=local/carlosxabier:/tmp/.ICE-unix/5106
SHELL=/bin/bash
SHELLOPTS=braceexpand:emacs:hashall:histexpand:interactive-comments:monitor
SHLVL=1
SSH_AGENT_PID=5160
SSH_AUTH_SOCK=/tmp/ssh-qBdbLs5106/agent.5106
TERM=xterm
UID=1000
USER=carlosxabier
USERNAME=carlosxabier
WINDOWID=50331742
XAUTHORITY=/home/carlosxabier/.Xauthority
_=set
bash205='3.2.13(1)-release'
bash205b='3.2.13(1)-release'
bash3='3.2.13(1)-release'
_ImageMagick () 
{ 
    local prev;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -channel)
            COMPREPLY=($( compgen -W 'Red Green Blue Opacity \
                                Matte Cyan Magenta Yellow Black' -- $cur ));
            return 0
        ;;
        -colormap)
            COMPREPLY=($( compgen -W 'shared private' -- $cur ));
            return 0
        ;;
        -colorspace)
            COMPREPLY=($( compgen -W 'GRAY OHTA RGB Transparent \
--Más--

Is this specific of ubuntu?.

---

### Post by jfinkels on 2007-11-15
As bingoUV said above,
> **bingoUV said:**
> set shows all keywords, ***including functions*** that are defined in your environment.

The "code" you are seeing is a function definition.

---

### Post by bingoUV on 2007-11-16
> **jfinkels said:**
> As bingoUV said above,


The "code" you are seeing is a function definition.

Yes, and I see it in fedora too, so it is not ubuntu specific

---

### Post by dreadrea on 2007-11-18
Thanks.:)

---

