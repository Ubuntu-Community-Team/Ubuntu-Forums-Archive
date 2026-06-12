---
title: "Reinstalling Grub From Alternate CD?"
date: 2008-05-09
forum: General Help
---

### Post by theytookpenny on 2008-05-09
I have had my ibook for about a year now (of and on with the Ubuntu up until about five months ago) and I have not had any real issue. Even now I do not, it is just that it bothers me that the usplash does not show up on boot up.

This happened to me when I tried to install a custom usplash from gnome-look.org. I, like an idiot, forgot to back up the menu.lst file and now it is missing and the usplash does not work. I've seen threads concerning this same issue, only their solutions involve the Ubuntu live cd. What I want to do is reinstall menu.lst through the alternate install cd.

Also, if I do manage to fix this issue, is there a way to bootup Ubuntu without showing any text at all and showing the usplash only?

Thanks in advance,
Jenny

---

### Post by adult swim on 2008-05-09
can you post your menu.lst here?
if youre not sure how to do that, hit alt-f2 and type in gksudo gedit /boot/grub/menu.lst

---

### Post by theytookpenny on 2008-05-09
Acutally, the menu.lst file is completely missing. Somehow, I'm still able to boot though.

---

### Post by adult swim on 2008-05-09
are you able to choose between osx and ubuntu on startup?

---

### Post by theytookpenny on 2008-05-09
Actually, I only have ubuntu installed.

---

### Post by adult swim on 2008-05-09
try running ```
sudo update-grub
``` from a terminal
then see if you have a new menu.lst

---

### Post by theytookpenny on 2008-05-09
When I do that, I get this error:

grub-probe: error: /boot/grub/device.map:1: Bad device name

---

### Post by logos34 on 2008-05-09
> **theytookpenny said:**
> When I do that, I get this error:

grub-probe: error: /boot/grub/device.map:1: Bad device name

the menu.lst has to be somewhere, otherwise you couldn't boot into ubu

post your

/boot/grub/device.map 

also look in /boot/grub for menu.lst~ file

---

### Post by adult swim on 2008-05-09
im not sure about that then.  if you can get access to a livecd (i know you mentioned that above) this is a good tutorial to reinstall grub and your setup [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351).  alternatively, you could try using the super grub disk, [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/), to reinstall grub.  im pretty sure the reason you are seeing text instead of splash on startup is that "ro quiet splash" was removed from your boot entry in grub.  im sure there are some grub pros that could offer you some better solutions, and if its not that big of a deal looking at text on startup, you might want to do that! good luck

---

### Post by theytookpenny on 2008-05-09
i've tried looking for it already with ctrl H, but its not there.

device.map shows this:
```
(/pci@f4000000/ata-6@d/disk@0)    /dev/hda
```

EDIT:
I went to partition editor to check the names of my partitions and I noticed that /dev/hda2 is flagged with "boot" I don't know if I should go and change this, but this is just a note to have.

---

### Post by logos34 on 2008-05-09
if that's your only hard disk, it should read

> (hd0) /dev/hda

then try to run sudo update-grub again

---

### Post by adult swim on 2008-05-09
totally unrelated to the op, logos your sig is hilarious!

---

### Post by logos34 on 2008-05-09
> **adult swim said:**
> totally unrelated to the op, logos your sig is hilarious!

yeah, it's so bad it's funny. can't remember now where I came across it

---

### Post by theytookpenny on 2008-05-09
> **logos34 said:**
> if that's your only hard disk, it should read



then try to run sudo update-grub again

Well it made a grub.cfg, I'm not sure if that's an equivalent to a menu.lst... but I'm afraid to restart my computer

EDIT:

Ok, I restarted my computer, and now the screen is flashing of and on with no usplash. When it loads gnome, the screen stays blank. I really need this computer, so I might just end up reinstalling ubuntu. Thanks for the effort, next time I'll just try to get my hands on a livecd.

---

### Post by zvacet on 2008-05-09
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") If configuring the network with DHCP failed,don´t worry.Continue and in next step select not configuring network now (or something similar).

---

