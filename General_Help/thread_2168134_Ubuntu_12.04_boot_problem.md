---
title: "Ubuntu 12.04 boot problem"
date: 2013-08-16
forum: General Help
---

### Post by gelty on 2013-08-16
Hey, I'm having some problems booting my pc. It says hd0 out of disc and won't boot. I tried boot repair several times, no help. Here is my boot repair info link: [http://paste.ubuntu.com/5993346/](http://paste.ubuntu.com/5993346/)

---

### Post by oldfred on 2013-08-16
From grub menu, use e and add disk-module=ata in place of quiet splash on linux line. If that boots then you can permanent add it with Boot-Repair or editing /etc/default/grub.

    
Out of disk error add to grub install disk-module=ata or use Boot-Repair ATA Disk support.

Some BIOS seem to have issues with boot files beyond some point on drive which we usually see as 100GB or 137GB. But all your boot files are inside the first 100, see line 580 in your BootInfo report.

Unrelated you may want to houseclean some older kernels. I like to keep current and one older and purge older. I prefer to use synaptic.


 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by gelty on 2013-08-16
The message appears before grub menu appears, so cant get that far. Any ideas?

---

### Post by sam_baker2 on 2013-08-16
Have you tried to let gparted fix it? 
I have had several problems in the past with booting and I ran the 
xubuntu install .iso in the cd and I let gparted check the partitions
on the HD, and gparted would say that there were problems and ask if
I wanted gparted to try to fix them. Both times gparted fixed it.

---

