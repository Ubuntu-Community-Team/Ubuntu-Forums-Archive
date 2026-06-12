---
title: "Weird yellow stripes on my display"
date: 2007-08-03
forum: General Help
---

### Post by davbren on 2007-08-03
Hi, I'm having this problem. I've just installed ubuntu on a fresh pc, I was using my monitor from my pc, and then i switched to my mothers 17" TFT with which the pc will be used. I have attached a picture and I hope you can see my problem.:S:S Its possible it won't show up on your screen.

---

### Post by ReaderRat on 2007-08-03
If you used the** old** monitor when you installed Ubuntu, then Ubuntu loaded the drivers for the **old** monitor. You needed to install using the **new** monitor to get the right drivers.

---

### Post by davbren on 2007-08-09
Should that matter? I thought monitors were plug and play...

---

### Post by splintercellguy on 2007-08-09
sudo dpkg-reconfigure -phigh xserver-xorg? Be sure to backup /etc/X11/xorg.conf beforehand by doing sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak and restore it should the X server fail to start by doing sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf.

---

### Post by davbren on 2007-08-09
whats the -phigh?? ive reconfigure the xserver thingy before with no luck, but i've never seen the -phigh bit in the command before

---

### Post by worty on 2007-08-10
Hey everyone, 

I'm having a similar problem as described but mine seems to be software based. I reconfigured xserver-xorg but that didn't seem to do much. I attached a screenshot.

---

