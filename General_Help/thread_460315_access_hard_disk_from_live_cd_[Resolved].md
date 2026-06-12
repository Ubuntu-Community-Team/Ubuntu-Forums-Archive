---
title: "access hard disk from live cd [Resolved]"
date: 2007-05-31
forum: General Help
---

### Post by molsen on 2007-05-31
how would i go about editing my xorg.conf on the hard disk from the live cd?  xubuntu 7.04

i tried

```
sudo mousepad /etc/X11/xorg.conf
```  but that just opens the one from the cd.  how can i access the hard disk version?

i ask this because i made a minor edit to my xorg, rebooted, and was not delighted to find that i had a "" in there instead of "....this is causing problems of course.....i can't boot my installed version

help please?

maybe linux isn't for me....i'm messing up left and right....

---

### Post by aysiu on 2007-05-31
**Warning**: Don't do *sudo mousepad*. *sudo* is for terminal applications. *gksudo* is for graphical ones. More details here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

**Method 1**: You can edit the /etc/X11/xorg.conf file without using the live CD. Just boot into recovery mode and type ```
nano -B /etc/X11/xorg.conf
``` This will open it up in the *nano* text editor. When you're done, save (Control-X, Y, Enter) and type ```
reboot
``` and boot into regular (not recovery) mode.

**Method 2**: If you're going to use the live CD, mount the hard drive first. I believe you can do this by just clicking or right-clicking the drive in the sidebar of the Thunar window. If not, we'll have to use the terminal to mount it. Once you've mounted it, close regular Thunar and launch Thunar as root by pressing Alt-F2 and typing ```
gksudo thunar
``` Then navigate to the mounted drive and edit the /etc/X11/xorg.conf file.

---

### Post by molsen on 2007-05-31
ahhh that makes sense.  thanks a bunch!  i will report back hopefully from my installed version....

---

### Post by molsen on 2007-05-31
great success!  i used the first method and it worked perfectly.

it's amazing how one extra quotation mark can nearly FUBAR the whole thing.  anyways, now i have my touchpad almost configured how i want. 

thanks again,
matt

---

