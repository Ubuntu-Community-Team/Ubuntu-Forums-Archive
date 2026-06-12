---
title: "New monitor/video card..."
date: 2006-12-14
forum: General Help
---

### Post by FluxCapacitor on 2006-12-14
Ok, I'm a bit new to this linux (as a desktop) thing.  I support Redhat servers for work, anyway, that's a different story.  So today my new monitor arrives and i already have a video card that I am upgrading to.  The make/model isn't as important as the procedure here.  I installed the new pci-e card and connected it to the new monitor with a dvi cable.  Well, I should've known better than to think that it would just work after turning the existing installation of Ubuntu back on.  It did not.  I got an error saying that there are no screens available.  So, with that said, what is the correct procedure to remove the drivers for an old monitor/vid card and install a new one as painlessly as possible?  Sorry if this seems like a noob question, but any help is greatly appreciated.

---

### Post by adaptr on 2006-12-14
It will depend for 90% on how you installed the previous video card, and whether you have changed manufacturers.

(You don't "install" a monitor, as the PC has no idea what you decide connect to it - and, indeed, couldn't care less.)

Just repeat the steps you followed the last time, substituting reasonable values for the new hardware in the xorg.conf file.

---

### Post by amoore on 2006-12-14
I know this won't help right now. :-( But I can't wait for bullet-proof X!!!! So people upgrading their video cards or other devices won't have this problem.

---

### Post by adaptr on 2006-12-14
I don't know what you mean by "bullet-proof".
X will perform very dependably when you configure your hardware correctly.
Would you rather exchange Ubuntu for that other OS, knowing that automatic driver installation is about the* only* thing it does right ?

Regardless, the fact that you call this - completely obvious - behaviour a "problem" shows how long you still have to go... :)

---

### Post by FluxCapacitor on 2006-12-14
Ok, here's the deal... the vid card is a nice new nvidia with dual dvi outputs (and some other round input/output)... anyway, I am unsure of the exact model of it, and without the proper documentation that came with it, I will not be able to find out.  I suppose I could find some obscure serial number on the card somewhere and look it up on google... but I was more leaning toward the idea that  there may be a way to "prepare" ubuntu for some new hardware coming in.  I know the monitor isn't so important here.  I just want to essentially "remove" the old card and any records of it from the OS, and install the new one, or have the system behave in a manner where it will maybe "accept" a new one... like safe mode or something along those lines.  The problem is, I do not know how to make this work.

---

### Post by FluxCapacitor on 2006-12-16
bump, c'mon I still need some help.

---

### Post by taurus on 2006-12-16
Boot into recovery mode from GRUB menu and reconfigure X again for your new video card and monitor.

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

