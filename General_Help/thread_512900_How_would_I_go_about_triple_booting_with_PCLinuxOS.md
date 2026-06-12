---
title: "How would I go about triple booting with PCLinuxOS, Windows and Ubuntu?"
date: 2007-07-29
forum: General Help
---

### Post by EvenStevens on 2007-07-29
But switch from the Ubuntu GRUB menu to the PCLinux one (it looks nicer as I've seen from my friend's computer)

I already have Ubuntu Feisty and Windows XP installed.
I'm dabbling in the KDE side of things now with PCLinux... but I'm scared to install it as when it gets to the GRUB stage of the installer, it seems to not want to recognise the Ubuntu install. Only XP and itself.
So I quit out. 

What could I do?

Thanks!

---

### Post by methinks on 2007-07-29
If you have a spare partition, you should be able to just install pclinux alongside ubuntu and windows.
As long as PCLinux is installed last, it's boot-loader (called Lilo) should automatically replace Ubuntu's boot-loader (called Grub)

---

### Post by confused57 on 2007-07-29
> **EvenStevens said:**
> But switch from the Ubuntu GRUB menu to the PCLinux one (it looks nicer as I've seen from my friend's computer)

I already have Ubuntu Feisty and Windows XP installed.
I'm dabbling in the KDE side of things now with PCLinux... but I'm scared to install it as when it gets to the GRUB stage of the installer, it seems to not want to recognise the Ubuntu install. Only XP and itself.
So I quit out. 

What could I do?

Thanks!
You should be able to go ahead and install PCLinuxOS grub to the mbr, then you can add an entry to boot Feisty, I would recommend a configfile entry:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

If you decide later on that you prefer Feisty's grub, you can install it with the live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

Added:  Here is how you would add a Feisty entry...open a Konsole:
```
su
cd /boot/grub
cp menu.lst menu.lst_backup
kwrite menu.lst
```
then add your Feisty configfile entry to the very end of the file:
```
title        Feisty on /dev/sda2
configfile   (hd0,1)/boot/grub/menu.lst
```
substitute your root for (hd0,1)...then quit & save

---

### Post by EvenStevens on 2007-07-30
Uhm..

Okay, I installed PCLinux, Rebooted and I still get the Ubuntu GRUB menu complete with Ubuntu kernels and Windows XP...but no PCLinux :|

Halp!

---

### Post by kelvin spratt on 2007-07-30
the only way i got this set up to work was to install Pclinux before ubuntu, i had problems there is also a slight problem in the installer in Pclinux writing to grub if it does not show other O/s step back in grub,

---

### Post by confused57 on 2007-07-30
> **EvenStevens said:**
> Uhm..

Okay, I installed PCLinux, Rebooted and I still get the Ubuntu GRUB menu complete with Ubuntu kernels and Windows XP...but no PCLinux :|

Halp!
In my other reply, there is a link to install Feisty's grub to the mbr, using the live cd...this can also be used to install PCLinuxOS's grub to the mbr.  If PCLinux installed correctly, "find /boot/grub/stage1" should return something like:
```
root (hd0,1) <------Feisty's root partition
root (hd0,3) <-----PCLinux's root partition
```

Using the above example, to install PCLinux grub to the mbr:
```
sudo grub
root (hd0,3)
setup (hd0)
quit
```

Then read back through my other reply for adding an entry to boot Feisty.

If "find /boot/grub/stage1" only returns one root partition, then PCLinux didn't install correctly(or grub wasn't installed)...in that case, reinstalling PCLinux would be the best option...

---

### Post by EvenStevens on 2007-07-30
Typing that into an Ubuntu terminal only brings up the words "/boot/grub/stage1" after pressing Enter.
Or do I need to type it into a PCLinuxOS konsole through the liveCD?

---

### Post by EvenStevens on 2007-07-30
Typing that into an Ubuntu terminal only brings up the words "/boot/grub/stage1" after pressing Enter.
Or do I need to type it into a PCLinuxOS konsole through the liveCD?

---

### Post by confused57 on 2007-07-31
> **EvenStevens said:**
> Typing that into an Ubuntu terminal only brings up the words "/boot/grub/stage1" after pressing Enter.
Or do I need to type it into a PCLinuxOS konsole through the liveCD?
It's my understanding that you want to use PCLinuxOS grub to boot Windows & Feisty.  What you want to do is boot up the Ubuntu live cd, open a terminal, enter:
```
sudo grub
find /boot/grub/stage1
```
you should get results for the root partitions of Feisty & PCLinuxOS, whichever is the root partition for PCLinuxOS, enter:
```
root (hdx,y)
setup (hd0)
quit
```
substitute (hdx,y) for your PCLinux root partition

This should install PCLinuxOS grub's IPL to the mbr, then see my other post for using a configfile to boot Feisty.

---

