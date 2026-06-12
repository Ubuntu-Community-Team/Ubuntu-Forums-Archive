---
title: "what do you do with BIN files?"
date: 2007-05-08
forum: General Help
---

### Post by nerdman978 on 2007-05-08
I downloaded the ATI driver installer from here
[http://ati.de/support/drivers/linux/linux-radeon-prer200.html]("http://ati.de/support/drivers/linux/linux-radeon-prer200.html")
but I have no idea what to do with it! It doesn't run automatically or anything and I tried running it in the terminal.

---

### Post by NT4usB on 2007-05-08
...delete it and try this:
[http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html)

---

### Post by nerdman978 on 2007-05-09
I used the previously posted guide and followed all directions correctly and did everything. However, I rebooted and saw the all-too-familiar message "X server blah blah blah not working blah blah blah". So what do I do? Can I just run beryl without X? (I have it installed)

---

### Post by spankymasterc on 2007-05-09
you cant start your computer without X..... xserver-xorg is what tells your computer to display and commands and such im not expert but as long as you drivers for your video card are installed and you installed beryl correctly then you should be fine....

---

### Post by nerdman978 on 2007-05-09
Yes, but I can't really do anything about X right now because my GUI won't load. What can I do in the terminal to fix what I did without completely re-doing xserver.xorg?

---

### Post by spankymasterc on 2007-05-09
> What can I do in the terminal to fix what I did without completely re-doing xserver.xorg?

you make it sound like a long lengthy process lol its like 5-6 things and all you do is leave everything on default 

Yeah you have to redo xserver

do this in terminal (safe-mode if you want)

```
sudo dkpg-reconfigure xserver-xorg
```:guitar:

---

### Post by nerdman978 on 2007-05-09
Ok so I'm stuck with re-doing my xserver.xorg again? Damn. So what do I do when I have fixed it, logon and face the same problem because I redid my xorg.conf and now the drivers still don't work. And when the drivers don't work, beryl doesn't work. And when beryl doesn't work, well....

---

