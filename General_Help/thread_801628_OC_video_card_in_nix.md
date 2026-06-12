---
title: "OC video card in *nix"
date: 2008-05-20
forum: General Help
---

### Post by RJ Hythloday on 2008-05-20
Didn't know where else to put this
 
It seems like all the tools to over clock an AGP card are .exe does any one know if they'll work in wine?
 
ATI WINCLK
[http://www.techpowerup.com/downloads](http://www.techpowerup.com/downloads)
 
or 3d mark
[http://www.futuremark.com/download/3dmark2001/](http://www.futuremark.com/download/3dmark2001/)

---

### Post by Zorael on 2008-05-21
Likely not.

You can overclock Nvidia cards in the nvidia-settings tool if you add and enable the Coolbits option in your [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] file. This cannot be done with the nvidia-xconfig tool, but it's easily done with a text editor. (Reply to thread if that's the case.)

As for ATI cards, quick googling turns up **rovclock**; [http://www.linuxmonitor.net/blog/2007/03/overclocking-ati-radeon-cards-in-linux.html](http://www.linuxmonitor.net/blog/2007/03/overclocking-ati-radeon-cards-in-linux.html).

---

### Post by RJ Hythloday on 2008-05-21
Thanks, I'll check out rovclock, looks like a good place to start.

---

