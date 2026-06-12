---
title: "Ubuntu Server 12.04 will not boot"
date: 2013-11-30
forum: General Help
---

### Post by rosscosack on 2013-11-30
Hi

I am unable to boot my ubuntu server.

I have followed the instructions regarding rescue a broken system from the installation CD, mouning the root drive, installing grub and rebooting but now it just comes to a grub prompt.
grub> 

In my case the root drive (and the only one that would allow me to load a shell in it) was the root volume group

so I mounted it with 
```
mount /dev/mapper/server--vg-root /mnt
```

and then attempted to install grub
```
sudo grub-install &#8211;boot-directory=/mnt/boot /dev/mapper/server--vg-root
```
when I run this, I get some warnings along the lines of "This is a bad idea" "cannot install to a partitionless drive" 

I used the LVM partition guide on the initial install so I have three partitions sda1, sda2, sda5
assuming they are boot, main and swap

 as well as four vgs - mediashare, VMs, root, swap 

So I also tried mounting sda1 to /mnt (and /mnt/boot) and then installing to /sda 

Which installs successfully but when I reboot, I get to the grub promt instead of booting to the operating system as expected.

Is there a command that I have to issue at the grub prompt? according to my searches, it should just boot as normal?
What do I need to do to boot my operating system?

Thank you

---

### Post by rosscosack on 2013-11-30
I have also tried this command in the grub prompt
```
root (hd0,msdos1)
```
and I get the error
```
error: unknown command 'root'
```

to explain why I choose the above command when I type 
```
root (hd
```
and then press <tab> it (grub) adds a '0'
then I type a ',' <comma> and the hit <tab> again it lists the possible partitions as hd0,msdos1 and hd0,msdos5.
msdos1 has a ext2 filesystem and msdos5 has "Not a known filesystem"

---

### Post by rosscosack on 2013-11-30
Forget it, Am doing a fresh install

---

