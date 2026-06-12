---
title: "[SOLVED] Dual Boot Ubuntu/DSL"
date: 2007-09-24
forum: General Help
---

### Post by drsmaw on 2007-09-24
I have finally made the move to go MSfree! Ubuntu sucked up the whole drive and everything runs beautiful. I am going to install a WRT54G Linksys wireless router. I like to tinker a little bit with distros and would like to add DamnSmallLinux. I read some of the other threads on this but I need a little more clarity.
Like, how to setup Grub the right way, the first time I try to install DSL.
1) Should I install DSL before installing the wireless router?

2) What precautions do i need to take when install DSL?

3) What do i need to know before I install DSL on a dual boot with Ubuntu?

4) I have the driver for the router, what is the best method to apply the driver?

Thanks.
davehateMS

MSfree and Happy!

---

### Post by Adramelech on 2007-09-24
Why dont you install VirtualBox? that way you can install as many distros as you like without touching the hard drive partition table

---

### Post by drsmaw on 2007-09-24
I thought about it, but not that much, it does make sense instead of toying around with partitions.  I have never used any virtual desktop.  I'll look into it.  Would I be able to save my settings - ex. - Mydsl extensions?
Here i am racking my brain, thanks for the simplicity.

---

### Post by Shazaam on 2007-09-24
Hard drive install?
1. Router first that way it MIGHT be recognised by DSL.
2. Use your Ubuntu livecd to add an empty ext3 partition to the drive making the DSL install easier. Point the DSL installer to the new partition.
3. When DSL asks where to install grub (or LILO) install it to the DSL partition then boot Ubuntu and do a grub-update. Ubuntu should pick it up. If it doesn't you can manually add it to Ubuntu's menu.lst
4. Is it a LINUX driver?

---

### Post by Adramelech on 2007-09-24
INstalling virtualbox is really easy.

[Get virtualbox]("http://www.virtualbox.org/wiki/Downloads")

See under the section: **VirtualBox binaries**

Actually I have like 7 OS under virtualbox and they work just fine, testing 7 distros without virtualization would be a nightmare.

---

### Post by drsmaw on 2007-09-24
Shazaam

I'm pretty sure a linux driver was included.  I think I remember seeing an .inf file.  Now I am torn between using Virtualbox or installing DSL to my hard drive.  Would I lose any functionality using DSL on VirtualBox?
But, do i want to see if I can get DSL installed to my hard drive?
These questions keep boggling my brain.
Either way, i now have more info than when i started

---

### Post by Shazaam on 2007-09-24
To SAFELY try out a new OS you have a few options. Try it with a livecd, or use virtualization (VirtualBox, VMware, etc).
AFAIK .inf files are Windows only.
The only functionality you would lose is most virtualization programs use "virtual" hardware instead of actual physical hardware. Your OS could run fine using virtualization (and all virtual hardware recognised) but refuse to run on "real" hardware. It's a tossup.

---

### Post by drsmaw on 2007-09-24
Shazaam

I can definitely say I have had hardware issues with DSL, maybe I should stay with virtualization.  Searching around, I found I do not really need to use any driver.  Just to acces the router's address and I can setup from there.  
I think I'll leave the dual boot scenario to my laptop. 
It's just that itch that makes you want to download more, see how much you can create on a computer, and then wipe it out and re-try something else.  I'm sick, I love it.

Thanks

---

### Post by Shazaam on 2007-09-24
For some light reading look at this...
[http://ubuntuforums.org/showthread.php?t=508061](http://ubuntuforums.org/showthread.php?t=508061)

---

