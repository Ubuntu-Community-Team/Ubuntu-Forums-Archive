---
title: "Cant re-install grub after trynig to dual boot."
date: 2007-06-27
forum: General Help
---

### Post by EYEdROP on 2007-06-27
So I wanted to have windows on my machine for work. I went through  this tutorial since it is identical to my system setup. I used the Gparted live cd and shrinked the ubuntu partition, which was using the whole disk. I made it 2 34 GB partitions. I unchecked the boot flag on the main Linux partition. Then I installed vista on the other unallocated partition, and everything went swell. Then I was ready to modify the Vista boot loader with my Ubuntu 6.10 live CD via the terminal. Refer to the "re-install grub" section. Here is my terminal output:


ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
(hd0,1)
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0,0)
setup (hd0,0)

Error 17: Cannot mount selected partition
grub>


I cant get past the setup (hd... command, I must be doing something wrong,

I really need help with this, I HAVE to get into Ubuntu ASAP. Help is very much appreciated. Thanks.

---

### Post by EYEdROP on 2007-06-27
toutorial: [http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

---

### Post by confused57 on 2007-06-27
Boot the live cd, & post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

In you output you listed, if "find /boot/grub/stage1" returned "root (hd0,1)", then you would:
```
root (hd0,1)
setup (hd0,1)
```

if you're wanting to install grub to the root partition...post the output of "sudo fdisk -l", before you attempt this, just in case you partition designation has changed.

---

### Post by EYEdROP on 2007-06-27
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.9 GB, 250999111168 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37558272    7  HPFS/NTFS
/dev/hda2            4677        9352    37559970   83  Linux
/dev/hda3            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by EYEdROP on 2007-06-27
perfect, I got the root and setup commands working. Ill update you if I have later difficulties.

---

### Post by EYEdROP on 2007-06-27
Okay, I got easybcd installed and set everything up perfectly. Now I try to boot into linux (which now has grub) and it says : Error 17: cannot mount disk. Any ideas?

---

### Post by confused57 on 2007-06-27
> **EYEdROP said:**
> Okay, I got easybcd installed and set everything up perfectly. Now I try to boot into linux (which now has grub) and it says : Error 17: cannot mount disk. Any ideas?
May not be the problem, but your root partition's UUID has probably changed since you resized it...you can mount your root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

you can then access your /etc/fstab and compare the UUID's with the output of:
```
blkid
```

[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by Computer Guru on 2007-06-29
Probably easier to just modify fstab to use /dev/sd*x* instead of UUID values.....

---

