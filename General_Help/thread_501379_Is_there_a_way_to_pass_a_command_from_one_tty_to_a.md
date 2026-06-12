---
title: "Is there a way to pass a command from one tty to another?"
date: 2007-07-15
forum: General Help
---

### Post by viciouslime on 2007-07-15
Is there a way I can run a command/program in tty1 and have it run as though I had typed it in tty2, or tty7....

For example if compiz had locked up, could i go to tty1 then type something to send "metacity --replace" to tty7?

---

### Post by jyba on 2007-07-15
If you know the file name of the terminal you want to send a command to you can redirect a command to it. Say you've got two terminals open, each running a bash shell. Type "tty" in each of them to find out their file name (or use "ps a" and work it out from there). If terminal-one is using **/dev/pts/0** and terminal-2 is using **/dev/pts/1** you can type...
```
echo 'Hi, this is terminal-one here!' > /dev/pts/1
```
...into terminal-one and the output will appear in terminal-two.

---

### Post by tgalati4 on 2007-07-15
When you get a compiz lockup, does control-alt-backspace not drop you to a command line?

---

### Post by viciouslime on 2007-07-16
> **tgalati4 said:**
> When you get a compiz lockup, does control-alt-backspace not drop you to a command line?

Well usually it would, it wasn't just for that though it was just out of interest really. Also, thinkgs like suspend/resume tend to lock compiz completely, leaving me with nothing but a pointer and a black screen :(

---

