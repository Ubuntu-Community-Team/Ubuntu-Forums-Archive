---
title: "Xorg Broke - Need Fix"
date: 2007-01-24
forum: General Help
---

### Post by iXneonXi on 2007-01-24
I've been runing Xubuntu 6.06 fine for a while.  I have not done any major upgrades lately.  However I may have done some upgrades.

When turning on my computer this morning X failed to start.
I use a Radeon 7000 PCI video card.

Please help me get my GUI back.

Logs and conf files attached for your convenience.

I'll be watching this thread quite frequently as I need this computer back up and running.  Any questions please ask, I'll reply as fast a possible.

---

### Post by geep on 2007-01-24
Can you post a little more information like log files ?

---

### Post by Twin Penguins on 2007-01-24
Im not totally sure but maybe this will help as I have trashed my xorg-conf many times and had to fix it.


$Sudo dpkg-reconfigure xserver-xorg

---

### Post by AndyCooll on 2007-01-24
Run the following:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo dpkg-reconfigure xserver-xorg
```

When you get to the graphics card section, choose "vesa". This is a bog standard graphics card setting that works with almost any settings. Once you get that running you can then play around and find an optimum setting.

:cool:

---

### Post by geep on 2007-01-24
are the ati drivers installed correctly ?

try to comment out ( # ) the horiz&vertical Sync and let xorg try and find the correct values ? 

i see a strange value at the BUSID but that doesn't have to be the problem

---

### Post by geep on 2007-01-24
sorry for the multi posts :). I def see a change in the BUSID i should look at that if i was you

---

### Post by mid_night gypsy on 2007-01-24
iXneonXi,
 Howdy,It looks like you have change monitors,and addedHorizSync,VertRefresh. they seem a little to low to me.remove them for now,and change the monitor back to a GATEWAY VX90,also change your busid back to the old one . hope this helps gypsy

---

### Post by iXneonXi on 2007-01-24
I'm changing the BUSID back and fixing the monitor section.  Going to reboot soon.  I don't think it is the ati drivers because I've been using them since install without hiccup until now.

If this does not work I'll try and reconfigure.

[EDIT] FIXED: Changing BUSID back, monitor back, and setting vsync and hsync to the monitor specifications, I was able to restore Xorg.  I had to add 1280x1024 back to depth 24 to return to my preferred resolution.
Thanks.

---

### Post by mid_night gypsy on 2007-01-24
You are welcome.

---

