---
title: "Installed nVidia drivers, now TTY's are blank?"
date: 2013-07-31
forum: General Help
---

### Post by Nor9864 on 2013-07-31
So after installing the nVidia drivers through the extra drivers package in the software center, my TTY's(Virtual Consoles) are all blank. They seem to have a low resolution and I can see a flashing underscore( _ ), but no login prompt or anything appears. This is really strange and it happends to all of them. I've already tried [one fix]("http://askubuntu.com/questions/162535/why-does-switching-to-the-tty-give-me-a-blank-screen") which didn't help. I use them quite a lot as I am not a big fan of starting the Terminal application, and I've had applications crash on me and whatever I did, I couldn't get back to the desktop, so my only option was to go to one of the Virtual Consoles and terminate it using htop. 

Any help or suggestions would be VERY appriciated! :)

---

### Post by Nor9864 on 2013-08-02
bump

---

### Post by sudodus on 2013-08-02
Do you want to keep the nvidia driver? Then you may have to live without the virtual consoles (it seems that the nvidia driver is not quite compatible with your hardware).

If the only thing you want to do is soft reset, there is also also this method
[B][I]
SysRq + r e i s u b[/I][/B]

according to this link

[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

> 
[LIST=1]
[*]Hold down the Alt and SysRq (Print Screen) keys.
[*]While holding those down, type the following keys in order, several seconds apart: REISUB
[*]Computer should reboot.
[/LIST]


Otherwise I suggest that you uninstall (remove) the nvidia driver (and maybe try another one).

---

### Post by steeldriver on 2013-08-02
I remember having the same problem with this nvidia-based laptop - the workaround I found at the time was to unblacklist the nvidia frambuffer device by commenting out the line in /etc/modprobe.d/blacklist-framebuffer.conf. However I haven't had to do that recently, so either it's an issue with only certain driver releases or (more likely, I think) I've now got a supported mode defined correctly in my grub config - I'd suggest trying that first i.e.

[LIST]
[*]boot into grub and run 'vbeinfo' at the grub prompt to see the available console modes 
[*]boot into the system normally and edit your /etc/default/grub to set the chosen mode e.g. for my laptop (which has a 16x10 screen) I have 
[/LIST]
[INDENT]```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1440x900
GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD=keep

```
[/INDENT]

[LIST]
[*]run ```
sudo update-grub
``` 
[/LIST]

I don't really understand how grub interacts with the virtual terminal modes but the 'GRUB_GFXPAYLOAD=keep' seems to be the key

---

