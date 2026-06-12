---
title: "Grub, Error 21"
date: 2008-01-30
forum: General Help
---

### Post by Wickedz on 2008-01-30
Hey there, I have a problem with Grub when I boot my computer.
So here is the deal. I have Windows XP on my internal HDD, and decided to put Ubuntu 7.10 an external HDD, however, when I rebooted without the eHDD (which I will need the other partition for school) I got error 21, I also think I got error 17 at some point. So anyways, what I'd like is that I can boot my Windows XP normally without the eHDD being connected, and when I need Ubuntu or whatnot I just change the boot priority.

Can someone help me out here?

Thanks, Mike

---

### Post by Wickedz on 2008-01-30
Please, someone help me out?!

---

### Post by confused57 on 2008-01-30
For Windows to boot normally without the external drive connected, you need to restore Windows IPL to your internal drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
If you have a Windows install cd(not a recovery cd),  boot your pc with the cd inserted, press "r", then FIXMBR...see the instructions in the above link.
If you don't have an install cd, you can use Super Grub Disk...use option "Fix Boot of Windows".

If your pc is capable of booting first to USB...boot the Ubuntu live cd & install grub's IPL to your external drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
something like:
```
root (hd1,0)
setup (hd1)
```

Then set your pc to boot first to the external hd, you should get a grub boot menu...make sure your first Ubuntu entry  is highlighted, press "e", select the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it is.  This change is temporary if it works, but it's no problem to make it permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Wickedz on 2008-01-30
I'll try this asap! Thanks so much

---

### Post by Wickedz on 2008-01-30
Thanks so much, my XP is fine now.

However, I'm left with a whole new problem.

I can't boot from my USB HDD. I'd like to know what I may or may not be able to do if possible =/

Thanks again

---

### Post by confused57 on 2008-01-30
> **Wickedz said:**
> Thanks so much, my XP is fine now.

However, I'm left with a whole new problem.

I can't boot from my USB HDD. I'd like to know what I may or may not be able to do if possible =/

Thanks again

Do you mean you're not able to set your bios to boot first to USB or that you're getting the grub boot menu, but not able to boot?  You may need to have your external HD connected to the same USB port when you installed Ubuntu.

Were you able to install grub's IPL to the external hard drive's mbr, using the live cd?

You could also try booting your USB drive, using Super Grub Disk or you could try a GAG floppy or cd:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
for GAG to work, grub's IPL needs to be installed to the root partition, using the live cd...something like:
```
root (hd1,0)
setup (hd1,0)
```

It may be a little inconvenient, but you may just want to use SGD or GAG to boot your external hard drive...you wouldn't need to change anything in your menu.lst in order to do this.

---

### Post by Wickedz on 2008-01-30
> **confused57 said:**
> Do you mean you're not able to set your bios to boot first to USB or that you're getting the grub boot menu, but not able to boot?  You may need to have your external HD connected to the same USB port when you installed Ubuntu.

What I mean is that in the boot menu the priority I thought necessary to boot from external HDD was "removable" because otherwise I don't have any other valid choices.

Basically, if I take away the option of booting from removable (which may be totally wrong on my part?)
then I'll just boot to Windows XP, on my internal HDD. If possible I'd like to boot from my external USB HDD as much on my own computer as on another computer, per say at school or a friends.

Is this idea conceivable? Thanks ahead of time

---

### Post by confused57 on 2008-01-30
> **Wickedz said:**
> What I mean is that in the boot menu the priority I thought necessary to boot from external HDD was "removable" because otherwise I don't have any other valid choices.

Basically, if I take away the option of booting from removable (which may be totally wrong on my part?)
then I'll just boot to Windows XP, on my internal HDD. If possible I'd like to boot from my external USB HDD as much on my own computer as on another computer, per say at school or a friends.

Is this idea conceivable? Thanks ahead of time
I've never set up an OS on an external USB drive, so I can't really advise you if removable means a USB device or not...

Obviously any other computer you want to boot Ubuntu on your external drive would need to be able to boot to USB first.  Why don't you try downloading & burning a copy of SGD(see the link in my first reply), then anytime you want to boot your external drive, insert SGD & select to boot Linux...you should be able to do this with other computers as well, although it may be difficult if the hardware is significantly different than your pc.  You might need to first boot into recovery mode and run:
```
dpkg-reconfigure xserver-xorg
```

GAG can also be installed to your internal drive's mbr...you would be able to boot Windows(even without your external drive connected) or your external drive with Ubuntu.  Then use SGD, if you want to boot the drive on another computer.

---

