---
title: "Filthy GRUB"
date: 2008-02-23
forum: General Help
---

### Post by sneakwit on 2008-02-23
Hello there!

Today I noticed a funny smell coming out of my computer. Because of this I turned off my computer and opened it up to see what the problem was. I worked out it was a problem with the PSU. I put in a new PSU, reconnected everything and booted up.

*BAM*

I get the grub error 22 screen. 

So, I tried to reinstall the GRUB using this - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

No luck :(


I used Super Grub Disk to try and fix it, which it partially did. Now I see the standard GRUB screen with a list of OSs -BUT- when I hit enter it comes up with the same "error 22" message.

I think it has something to do with the root (hd2,1) line in the GRUB. Maybe it's (GRUB) not pointing to the right partition or something?

I don't know if the following info is of any help -

-My ubuntu is installed on "/dev/sda2" (This is on the master drive)
-I have 3 HDDs. Two IDE and one SATA. The master is an IDE drive
-I dual boot with Windows XP
-Everything was running perfectly before today

I know this post isn't very clear, but I'm very tired. I'll try and fix this post up in the morning.

Thanks in advanced,

-Ross

---

### Post by Rhubarb on 2008-02-23
I suggest you boot from an ubuntu live cd, and just check to see if you can see all of your hard drives and partitions correctly.  Just to make sure your hard drives / motherboard etc is ok.

Then you can go about trying to restore grub.

---

### Post by imtheguru on 2008-02-23
Error 22 is a missing partition.

Verify whether your new power supply is powering all the hard drives.

---

### Post by philinux on 2008-02-23
I'd reinstall grub from the live cd if the power to the drives is ok.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by sneakwit on 2008-02-23
I've checked the power to the harddrives using the live cd. Everything seems to be fine. I can see my ubuntu partition an everything.

I looked at the drive map in my grub folder and it reads

```
(hd0)    /dev/hda
(hd1)   /dev/hdb
(hd2)  /dev/sda
```

My ubuntu partition is /dev/sda2. Does this mean the line in GRUB should read

```
root (hd2,**2**)
```

instead of

```
root (hd2,**1**)
```

-Ross

[B][COLOR="Red"]Edit: I've just tested this but I still get the same error. I just figured out 0 = partition 1 >_<

I KNOW the ubuntu partition is still there and everything. I've tried reinstalling GRUB from the live CD but it just doesn't work![/COLOR][/B]




[B][COLOR="Green"]Edit2: I figured out something was wrong when hd2 must have meant it (the Ubuntu partition) was on the second drive, when it was actually on the first drive. So I tried changing

```
root (hd2,**1**)
```

to

```
root (hd**0**,1)
```

Now it all works! All I've got to do is change it to boot from (hd0,1) in /boot/grub/menu.lst

Thanks Anyway!

-Ross  [/COLOR][/B]

---

