---
title: "Restart X Error/Flickering"
date: 2007-03-16
forum: General Help
---

### Post by covert215 on 2007-03-16
I am using 32-bit Feisty on a 64-bit AMD card.  I have an ATI card.  Whenever I press Ctrl-Alt-Backspace to restart X, I get taken to a terminal where X won't restart.  The screen will not stop flickering.  Sometimes I am able to type blindly and use the restartx command.

I have customized my xorg.conf, but this occurs even when I use the default.

If anyone has experienced this error or can help, I would greatly appreciate it.

---

### Post by ComputerGuy56 on 2007-03-16
Feisty is still in progress. Don't expect it to be perfect.

---

### Post by johnnymac on 2007-03-16
I have a very similar issue where if I do a ctrl-alt-backspace I get taken out to console without a prompt - and when I alt to another v-terminal and issue a restart of gdm or startx I get an error....so I stopped doing that :)

Right now Feisty is wicked Alpha - it's quite stable for an alpha - but still an alpha.  I'd check launchpad to see if it's reported.

---

### Post by covert215 on 2007-03-16
> Feisty is still in progress. Don't expect it to be perfect.

This is certainly a MAJOR error, and with a release in just over a month, it should probably be taken care of.  I don't expect perfection at all, but I would atleast prefer basic functionality.

---

### Post by jerrylamos on 2007-03-16
I'm pretty hung up too.  Ubuntu boots up in 1024x768 since it doesn't detect the memory on my Intel 845 card, so for  proper 1280x1024x24 I switch out of X, killall gdm, and run dpkg-reconfigure xserver-xorg which I can't do any more with 20070316.

Can't do that any more, because there isn't a prompt from either Ctrl-Alt-Backspace or Ctrl-Alt-F1.

Any ideas?  Note that PCLinuxOS, Freespire, Simply Mepis, ... all boot up in 1280x1024.

Thanks, Jerry:(

---

### Post by covert215 on 2007-03-16
Resolution may have something to do with it.  I'm in 1280x1024 as well.

Anyone have suggestions?

---

### Post by johnnymac on 2007-03-16
So I think this has already been said - Feisty is still "testing."  If you choose to run Feisty it's at your own risk.  I'd drop back to Edgy or wait for Feisty to be released.  Now - saying that.....here's some options:

First, what driver does xorg.conf have in the devices section for your video?  If it indicates the correct drive - there may be a bug there with the driver, set it as vesa and see what happens.

---

### Post by covert215 on 2007-03-16
```
Section "Device"
	Identifier	"ATI Radeon Express 200"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"UseFBDev"		"true"
EndSection
```

i'll give vesa a shot

edit: well, that fixed the flickering, but now i can't use 1280x1024 resolution
also, restarting x hangs on "Running local boot scripts (/etc/rc.local)"

edit again: that hang seems to be a common issue....

---

### Post by covert215 on 2007-03-17
help?

---

### Post by johnnymac on 2007-03-17
I'm not an ATI guy (I use NVidia) but may want to look around for installing the latest and greatest ATI stuff (if you haven't already).  Also, this could be fixed if you upgrade your dist:

```

sudo apt-get update ; sudo apt-get dist-upgrade

```

Also, if your trying to do beryl or compiz stuff you might want to disable that.

---

