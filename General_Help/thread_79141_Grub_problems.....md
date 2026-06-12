---
title: "Grub problems...."
date: 2005-10-19
forum: General Help
---

### Post by Zepticon on 2005-10-19
Hi...
I tried to install Kubuntu on my new harddrive. Its going Dualboot with XP home, who i already have on another disk. But after instaling Grub and everything is done, XP starts as default without prompting for Kubuntu?
Im using SATA if that has anything to do with it...

Please help?

---

### Post by djkork on 2005-10-19
if your windows starts without prompting... i think you haven't installed Grub well....
You need a Live CD to boot into your system...
After that you have to run grub

sudo grub

let's supose that you have only one HD, and 4 partitions

sda1 /boot
sda2 Windows
sda3 swap
sda4 /

then you have to say to grub where is your boot directory, to do this you have to
>root (hd0,0)

hd0 is your first harddisk, hd1 next .......
(hd0,0) is the first partition at the first hd... (hd0,1) second partition  
so, like my /boot is in the first partition of the first hd, then (hd0,0)

after that
>setup (hd0)
to say grub to install itself in the MBR of your disk

if all goes well
>quit
reboot your computer

I hope this helps.....

---

### Post by Saarg on 2005-10-19
If the old HD is ide you need to set sata to boot in your bios.

---

