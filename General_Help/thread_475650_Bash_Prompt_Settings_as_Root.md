---
title: "Bash Prompt Settings as Root"
date: 2007-06-16
forum: General Help
---

### Post by drs305 on 2007-06-16
I am trying to change the root prompt display.

When I run as root (sudo su) my prompt turns red & blue. I have customized prompt settings in ~/.bashrc that work whenever I'm not root. There are default lines in .bashrc for setting colors in root, but changes I make there don't seem to take effect. I've even deleted the entire contents of .bashrc and the color root prompt appears. That more or less makes sense to me in that if I'm working as root it would not pay attention to what was written in a user .bashrc 

I've tried ammending or deleting lines in ~/.bashrc, ~/.profile, /etc/profile, and /etc/.bash.bashrc and none of them appear to control the 'root' prompt.

FYI, the current root display is:
```
\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$
```

Please tell me what file contains the prompt formatting while running terminal as root.  Thanks.

---

### Post by ib80 on 2007-06-16
Did you try editing the .bashrc file in /root/ ? It works for me when I do aliases. Didn't try it for the prompt though.

But I also have an issue ;) :

I want the rm and cp commands to have the -i option turned on by default when I run sudo. Not sudo su, just "sudo rm []" or "sudo cp []"
I've setup both .bashrc's (using alias) user+root. But the root one is not taken into consideration when I use sudo.

Any suggestions ?
Thx,
ib

---

### Post by drs305 on 2007-06-18
Thanks ib80, that did it. Maybe someone can answer your question.

---

