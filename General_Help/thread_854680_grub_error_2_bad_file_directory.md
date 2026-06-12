---
title: "grub error 2: bad file directory"
date: 2008-07-09
forum: General Help
---

### Post by Activist on 2008-07-09
hello, i have 2 hard disks, one with windows and the other with ubuntu installed...

today in the ubuntu hard drive i created a partition (sda3) to setup gentoo, just to try it...
i now am finished with the installation, i have ubuntu properly mounting sda3 but i cant boot gentoo with grub (neither normal, nor rescue)... it says "bad file directory"...

in my /boot/grub/menu.lst
```
title		Gentoo 2008.0
# Partition where the kernel image (or operating system) is located
root		(hd0,2)
kernel		/boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=UUID=0e24ee7b-9c3d-4e23-83ba-05b91d8c968c
initrd		/boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

title Gentoo 2008.0 (rescue)
# Partition where the kernel image (or operating system) is located
root		(hd0,1)
kernel		/boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/sda3
initrd		/boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

```

output of fdisk -l:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6851    55030626   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda3            6852        9541    21607425   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

```

please help me ](*,)

---

### Post by Activist on 2008-07-09
up.. :S

---

### Post by VMC on 2008-07-09
What's the output of this, from a Terminal:

```
sudo blkid
```

---

### Post by Activist on 2008-07-09
/dev/sda1: UUID="d7463494-828c-46d3-baf6-f0d4cf02c569" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="41d91f5c-dc00-4a1e-8807-69cc28d74abf" 
/dev/sdb1: UUID="F44CAF244CAEE11A" TYPE="ntfs" 
/dev/sda3: UUID="0e24ee7b-9c3d-4e23-83ba-05b91d8c968c" SEC_TYPE="ext2" TYPE="ext3"

---

### Post by mcduck on 2008-07-10
Well, the rescue mode definitley doesn't work because your Grub entry specifies /dev/sda2, the extended partition, as it's root.. ;)

---

### Post by Herman on 2008-07-10
```
title        Gentoo 2008.0
# Partition where the kernel image (or operating system) is located
root        (hd0,2)
kernel        /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=UUID=0e24ee7b-9c3d-4e23-83ba-05b91d8c968c
initrd        /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5

title Gentoo 2008.0 (rescue)
# Partition where the kernel image (or operating system) is located
root        (hd0,1)
kernel        /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/sda3
initrd        /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5
```:) Hello Activist,
It's not necessary to use GRUB's kernel commands for booting the other Linux operating system directly, and if fact it's not the best way to dual or multi boot when you have more than one Linux.
You should use the chainloader command or the configfile command instead.
You can use the chainloader command if you have installed Gentoo's GRUB to the first sector of Gentoo's partition.
You can use the configfile command providing you have GRUB as Gentoo's boot loader, but not if you're booting Gentoo with LiLo.
Here's an example,
```
title           Gentoo 2008.0
configfile       (hd0,2)/boot/grub/grub.conf
```That will bring up Gentoo's own GRUB menu in Ubuntu's GRUB and you should be able to boot Gentoo from that.
Here's a link explaining more about how to multiple boot with other Linux installations, [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems").

Regards, Herman :)

---

### Post by Activist on 2008-07-10
first of all, i had already tried copying the settings from my GENTOO /boot/grub/grub.conf in my UBUNTU /boot/grub/menu.lst
(btw, my GENTOO /boot/grub/menu.lst is a link or something,and has the same text with grub.conf)

this is what i did in my ubuntu menu.lst
> 
title		Gentoo Linux 1
root		(hd0,2)
chainloader	+1
this gave me error: Invalid or unsupported executable format


okay, and just to understand more of the situation... the problem is only the GRUB itself right? not any GENTOO /etc/fstab etc... cuz im not quite sure if i got the swap set ok, etc...
> title		Gentoo Linux 2
# Partition where the kernel image (or operating system) is located
root		(hd0,2)
kernel		/boot/kernel-2.6.24-gentoo-r5 root=/dev/sda3

title		Gentoo Linux 3
configfile	(hd0,2)/boot/grub/grub.conf
and these two gave me error bad file or directory  :S
herman, how do i know if GENTOO grub is on the 1st sector?

---

### Post by Activist on 2008-07-10
up :S

---

### Post by Activist on 2008-07-10
ok, i found out something weird, which might get us into something....

when the grub menu appears, if i press C to get me to command line, the output of
> find /etc/fstab is
(hd0,0)

but /etc/fstab exists in GENTOO also, so the output should be
(hd0,0)
(hd0,2)

the same goes for some other files that exist in both, for example /boot/grub/menu.lst

wtf is going on??

---

### Post by Herman on 2008-07-10
Maybe you need to run a file system check in your Gentoo partition(s).
```
sudo e2fsck -C0 -p -f -v /dev/sda3
```
[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").
Try a file system check, it's always good to run a file system check regardless of whether it's needed or not and it might solve your problems.

---

### Post by Herman on 2008-07-10
> first of all, i had already tried copying the settings from my GENTOO /boot/grub/grub.conf in my UBUNTU /boot/grub/menu.lst Yes, that should normally work.
> (btw, my GENTOO /boot/grub/menu.lst is a link or something,and has the same text with grub.conf) Yes, it is a symlink, I visited Gentoo Web Forums and searched GRUB posts and did a little research there.

> this is what i did in my ubuntu menu.lst
     Quote:
                                                 title        Gentoo Linux 1
root        (hd0,2)
chainloader    +1                                 
this gave me error: Invalid or unsupported executable format
Your idea to try chainloading is a good idea. If Gentoo uses a greatly modified GRUB, and it's too much different from Ubuntu's GRUB, the configfile method might not work. You should be at least able to chainload Gentoo's GRUB from Ubuntu, but you will need to make sure Gentoo's GRUB is installed in the first sector of Gentoo's partition for that to work.
I don't know if Gentoo's GRUB is that much different from Ubuntu's GRUB or not, we use GNU/GRUB 0.97 and Gentoo uses GNU/GRUB 0.97 r5 I think. Maybe it is a lot different.
> herman, how do i know if GENTOO grub is on the 1st sector? Probably it isn't or your chainloader command would have booted it. 
Boot Ubuntu and  use Ubuntu to install Gentoo's GRUB to the first sector of your Gentoo partition,
```
sudo grub
find /boot/kernel-genkernel-x86-2.6.24-gentoo-r5
root (hd0,2)
setup (hd0,2)
quit
```Now try chainloading Gentoo again and it this time should boot.
> okay, and just to understand more of the situation... the problem is only the GRUB itself right? not any GENTOO /etc/fstab etc... cuz im not quite sure if i got the swap set ok, etc...It might not be a problem with GRUB, GRUB is a great debugging tool, it may well be that there's something else wrong, (such as a corrupted file system, a partition table problem or something like that). Hopefully the file system check I gave you in the post above this one will fix it.

---

### Post by rraj.be on 2008-07-10
Why not tp use super GRUB disk to boot now.

Just download it from here and burn it to a cd.

[linux.softpedia.com/get/System/Boot/Super-Grub-Disk]("linux.softpedia.com/get/System/Boot/Super-Grub-Disk")

You can use it to boot your system now.

---

### Post by kd5ful on 2008-07-10
> **rraj.be said:**
> Why not tp use super GRUB disk to boot now.

Just download it from here and burn it to a cd.

[linux.softpedia.com/get/System/Boot/Super-Grub-Disk]("linux.softpedia.com/get/System/Boot/Super-Grub-Disk")

You can use it to boot your system now.

Hello, Sir.

  That link was a dud.

Try this one:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

