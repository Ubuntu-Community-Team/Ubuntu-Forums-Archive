---
title: "Terminal made me mad"
date: 2008-03-04
forum: General Help
---

### Post by madara_sama on 2008-03-04
Hello there..
I got mad of using ubuntu (7.04). Cuz, the path of active directory on terminal.
How to set up terminal to hide its path, just the last active directory?
**$user@host mydir**          not         **$user@host /mydir/mydir/mydir**
What should I do to set it up?

---

### Post by lloyd_b on 2008-03-04
> **madara_sama said:**
> Hello there..
I got mad of using ubuntu (7.04). Cuz, the path of active directory on terminal.
How to set up terminal to hide its path, just the last active directory?
**$user@host mydir**          not         **$user@host /mydir/mydir/mydir**
What should I do to set it up?

First off, you're not entirely clear what you want changed.  Do you want to change the prompt, or the text in the window titlebar?

Either way, it involves editing the file ".bashrc" in your home directory.  To change the prompt, look for the lines
```
 case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]**\w**\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:**\w**\$ '
    ;;
esac
```
and change the "\w" (in bold) in the "PS1=..." lines to a "\W".

To change the window titlebar, look for the line
```
   PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
```
and change it to
```
     PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: `basename $PWD` \007"'
```

Lloyd B.

---

### Post by der_joachim on 2008-03-04
[This thread]("http://ubuntuforums.org/showthread.php?t=674446&highlight=bash+prompt+howto") will help you along. Short version: change the following line in your .bashrc 
```

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

```
to
```

PS1='${debian_chroot:+($debian_chroot)}\u@\h:\W\$ '

```
Notice the uppercase W at the end.

[edit]Oops! too late :) [/edit]

---

### Post by Oldsoldier2003 on 2008-03-04
more command prompt fun:
[http://www.expertsrt.com/tutorials/Matt/CmdPrompt.html](http://www.expertsrt.com/tutorials/Matt/CmdPrompt.html)
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by madara_sama on 2008-03-07
Thanks guys, you were freed my mad. These really help me.

---

