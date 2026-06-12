---
title: "Added extra hard drive, can't mount"
date: 2005-10-22
forum: General Help
---

### Post by ronin_ar on 2005-10-22
Hi all,

I'm running ubuntu without problems from 6 months now, I've installed a new hard drive ( I've installed winxp to do some gamming sorry! ), when the computer boot y select to boot from the hard drive where ubuntu is installed but when it starts to boot it says that can't mount /dev/sda7 - it does not exist says.

It then will give me an sh console, where I can see that my drives are now: 

sda1, sdb1 to sdb7.

So the question is how do I change / what do I change to make my current ubuntu install to boot again?

Thanks in advance!

---

### Post by Ocxic on 2005-10-22
[QUOTE=ronin_ar]Hi all,

I'm running ubuntu without problems from 6 months now, I've installed a new hard drive ( I've installed winxp to do some gamming sorry! ), when the computer boot y select to boot from the hard drive where ubuntu is installed but when it starts to boot it says that can't mount /dev/sda7 - it does not exist says.

It then will give me an sh console, where I can see that my drives are now: 

sda1, sdb1 to sdb7.

So the question is how do I change / what do I change to make my current ubuntu install to boot again?

Thanks in advance![/QUOTE]
 just as a test remove the new HD and see if it will boot properly, if it does, remove the mount point line from your fstab and try to mount it manually, and if the drive is NTFS that could be another reason why it's givin u problems. thats all i can think of.

AND... make sure you didn't accedently change your drive order by using CABLE SELECT on your drives, tho convienient it can cause these types of problems

---

### Post by ronin_ar on 2005-10-22
[QUOTE=Ocxic]just as a test remove the new HD and see if it will boot properly, if it does, remove the mount point line from your fstab and try to mount it manually, and if the drive is NTFS that could be another reason why it's givin u problems. thats all i can think of.

AND... make sure you didn't accedently change your drive order by using CABLE SELECT on your drives, tho convienient it can cause these types of problems[/QUOTE]

Yes, removing the new HD allowed me to boot.
The drives are both SATA and have no cable select option, the old one is attached to the same SATA port as always.

My motherboard gives me the option to select wich drive to boot, so what I want to do is to.
Have both drives as booteables, the problem is that when the new one is attached ubuntu is 'renaming' /dev/sda7 to /dev/sdb7 then it won't boot.

I don't know if this is doable, but any help will be appreciated.

---

### Post by ronin_ar on 2005-10-22
Do anyone knows if editing the file in /boot/grub/menu.lst and changing the parameters to be the new disk names can work?

---

### Post by ronin_ar on 2005-10-23
Yeah, changing that in menu.lst did the trick, and then I did a modification in /etc/fstab to get swap to work.

Cool!

---

