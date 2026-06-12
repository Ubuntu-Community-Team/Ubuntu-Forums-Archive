---
title: "* Starting anac(h)ronistic cron anacron...(system hangs during bootup)"
date: 2007-12-10
forum: General Help
---

### Post by theferno on 2007-12-10
i'm soo confused, my ubuntu desktop (version 7.10) was working fine, but now when I try to boot up it says:

* Starting anac(h)ronistic cron anacron                 [OK]
* Starting deffered execution scheduler atd         [OK]
* Starting periodic command scheduler crond        [OK]
* Checking battery state...                                    [OK]
* Running local boot scripts (/etc/rc.local)             [OK]

and then my computer just hangs... it was working fine yesterday, the only thing i changed was i moved my video card to a new pci slot because i had to make room for a network card to take up another pci slot, other than that everything is the same from when it was working

note: i can successfully boot into recovery mode and use the $ prompt


any ideas???

---

### Post by theferno on 2007-12-10
nevermind, right after i posted i noticed someone had the same problem on another post and it ended being the video card, to fix it you have to enter:

sudo dpkg-reconfigure -phigh xserver-xorg
sudo start x

[SOLVED]

---

### Post by eamonireland on 2008-03-23
Sorry, complete noob here, and struggling with understanding even how to interpret these terminal commands. I tried to enter the above command as follows
eamon@eamon-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080323135529
eamon@eamon-laptop:~$ sudo start x
start: Unknown job: x

Help.

---

### Post by KeyserSoze93 on 2008-03-23
I think he meant "sudo startx" (though you probably don't need the sudo)

---

