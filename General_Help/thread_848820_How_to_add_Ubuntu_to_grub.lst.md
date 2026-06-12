---
title: "How to add Ubuntu to grub.lst?"
date: 2008-07-03
forum: General Help
---

### Post by Scooter7 on 2008-07-03
Hi,

I'm currently running openSUSE 11.0 from my external HDD, with Ubuntu Hardy and WinXP on my laptop's internal HDD.

I'm trying to add Ubuntu to my menu.lst.   This is what I have at the moment:

```
# Modified by YaST2. Last modification on Fri Jun 27 02:27:55 UTC 2008
default 0
timeout 8
gfxmenu (hd0,1)/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.0 - 2.6.25.5-1.1
    root (hd0,1)
    kernel /vmlinuz-2.6.25.5-1.1-pae root=/dev/disk/by-id/usb-Ext_Hard_Disk_10000E000D650695-0:0-part2 resume=/dev/sda4 splash=silent showopts vga=0x314 acpi=off
    initrd /initrd-2.6.25.5-1.1-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.5-1.1
    root (hd0,1)
    kernel /vmlinuz-2.6.25.5-1.1-pae root=/dev/disk/by-id/usb-Ext_Hard_Disk_10000E000D650695-0:0-part2 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off x11failsafe vga=0x314
    initrd /initrd-2.6.25.5-1.1-pae

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1

title Ubuntu
     root (hd0,3)
     makeactive
     chainloader +1

```

When I choose my new entry in grub, I get 'error 13: invalid or unsupported executable format'.

What's the proper way to add Ubuntu to menu.lst?

Thanks,

---

### Post by AnarkistNZ on 2008-07-03
Something along the lines of this:

```

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,4)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

---

### Post by Scooter7 on 2008-07-03
Thanks, but that didn't work - I got something like 'cannot boot that partition' when using hd0,3 and 'file not found' with hd0,2 (I'm not sure which is my boot partition and which is my ubuntu partition).

---

### Post by tech0007 on 2008-07-03
'sudo update-grub'

---

### Post by confused57 on 2008-07-03
You could try something like:
```
title  Ubuntu 8.04
configfile (hd1,3)/boot/grub/menu.lst
```

or

```
title  Ubuntu 8.04
configfile (hd0,3)/boot/grub/menu.lst
```

---

### Post by Scooter7 on 2008-07-04
@tech007: Thanks, but I'm running openSUSE, so I don't have access to that command.

@confused57: Didn't work, I still get the 'cannot boot partition' error... I know Ubuntu is still there, as I can mount the partition from openSUSE.

---

### Post by erfahren on 2008-07-04
you can try the Symlink boot entry way - see my post here:
[http://ubuntuforums.org/showpost.php?p=4006408&postcount=4](http://ubuntuforums.org/showpost.php?p=4006408&postcount=4)

---

### Post by bodhi.zazen on 2008-07-04
can you tell us which is your Ubuntu partition ?

---

### Post by Scooter7 on 2008-07-04
Still no go.

What I don't get is this: in my menu.lst, in the entry for openSUSE:

```
title openSUSE 11.0 - 2.6.25.5-1.1
    root (hd0,1)
    kernel /vmlinuz-2.6.25.5-1.1-pae root=/dev/disk/by-id/usb-Ext_Hard_Disk_10000E000D650695-0:0-part2 resume=/dev/sda4 splash=silent showopts vga=0x314 acpi=off
    initrd /initrd-2.6.25.5-1.1-pae
```

The root is hd0,1.

The same is true with the entry for Windows:

```
title Windows
    rootnoverify (hd0,1)
    chainloader (hd0,0)+1
```

---

### Post by Scooter7 on 2008-07-10
Sorry for the double-post, but I figured if I just edited my post no one would see the change.   bohdi.zazen, I didn't see your post until now, we must have posted at the same time.

I'm pretty sure my Ubuntu partition is /dev/sda3, would that be hd0,3?

---

### Post by dracayr on 2008-07-10
not necessarily. in the grub prompt, type 

find /boot/grub/stage1

to find all partitions with linux installed on them. then rule out the partitions of which you know that you have a different linux installed, and the elusive ubuntu partition remains :)

dracayr

---

### Post by Scooter7 on 2008-07-10
The output was '(hd0,1)'.   The only Linux installations I have are my Ubuntu one (on my internal drive with Windows), and my openSUSE one, which is on my external drive.

Both use the same partition on my internal drive for their /boot partition - could that be a problem?   If Ubuntu's GRUB was overwritten by openSUSE's GRUB, could that keep me from booting Ubuntu?

---

### Post by bodhi.zazen on 2008-07-10
> **Scooter7 said:**
> The output was '(hd0,1)'.   The only Linux installations I have are my Ubuntu one (on my internal drive with Windows), and my openSUSE one, which is on my external drive.

Both use the same partition on my internal drive for their /boot partition - could that be a problem?   If Ubuntu's GRUB was overwritten by openSUSE's GRUB, could that keep me from booting Ubuntu?

Well, that most likely is the problem. Most distros overwrite /boot when you install.

Boot SUSE and 

```
ls /boot
```

Do you see your Ubuntu Kernels ? If not, they are gone.

If there are still there we can boot Ubuntu, but we need to know your partition scheme.

---

### Post by Scooter7 on 2008-07-10
Hmm, they don't seem to be there, no.

I'm not sure what they were called, though.   Here's the output:

```
backup_mbr               symsets-2.6.25.9-0.2-pae.tar.gz
boot                     symtypes-2.6.25.9-0.2-pae.gz
config-2.6.25.9-0.2-pae  symvers-2.6.25.9-0.2-pae.gz
grub                     System.map-2.6.25.9-0.2-pae
initrd                   vmlinux-2.6.25.9-0.2-pae.gz
initrd-2.6.25.9-0.2-pae  vmlinuz
lost+found               vmlinuz-2.6.25.9-0.2-pae
message
```

And here is my partition scheme, /dev/sda being my internal drive, /dev/sdb being my external:

```
/dev/sda1 - Windows XP
/dev/sda2 - GRUB/boot
/dev/sda3 - Ubuntu filesystem?
/dev/sda4 - swap

/dev/sdb1 - Storage
/dev/sdb2 - openSUSE root (I think)
/dev/sdb3 - Swap
/dev/sdb4 - openSUSE home (I think)
```

For the openSUSE partitions I'm not sure about, it could be the other way around (i.e, sdb2 could be home, sdb4 could be root).

Is it possible to install Ubuntu's kernels again without completely reinstalling Ubuntu?

---

### Post by bodhi.zazen on 2008-07-10
OUCH :(

Ok, my first piece of advice before you go much further is to do a little reading.

First you should know what your partitions are, both in standard linux + grub speak :twisted: :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

OK, next look at this thread re: Multibooting. I have to re-work that thread a little, but it goes through the basic issues :

[How to Multi-boot (Maintain more then 2 OS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=724817") 

OK, now you may be able to install the Ubuntu kernels, using chroot.

Boot the Ubuntu live CD, it will make life easier.

Assuming ubuntu root is /dev/sda3 and a boot partition of /dev/sda2 :

On the live CD, open a terminal and become root with ```
sudo -i
```

Now :

```
mount /dev/sda3 /mnt

mkdir /mnt/boot #It is OK if /mnt/boot already exists, just go on

mount /dev/sda2 /mnt/boot

chroot /mnt /bin/bash
```

Now install a kernel :

```
apt-get install linux-generic
```

Now update grub (still in the chroot)

```
nano /boot/grub/menu.lst
```

Enter these lines at the end :

> title Ubuntu
root (hd0,1)
kernel vmlinuz-xyz root=/dev/sda3 ro quiet splash
initrd intird-xyz
boot

You need to change "vmlinux-xyz" and "initrd-xyz" to your linux images.

Exit the chroot and reboot.

The problem will be when you update an Ubuntu Kernel you will almost certainly have problems (because grub is configured for SUSE).

So you may want to do all by making a boot directory in Ubuntu. This will involve installing grub as well and is a little more complex ...

If all this is greek to you, re-install Ubuntu following the links I gave you :twisted:

---

### Post by Scooter7 on 2008-07-10
Although I'm sure I can manage those steps, I think I'll just reinstall - probably a good idea anyway, since I can use those links you provided.

Thanks!

---

### Post by confused57 on 2008-07-10
> **Scooter7 said:**
> Sorry for the double-post, but I figured if I just edited my post no one would see the change.   bohdi.zazen, I didn't see your post until now, we must have posted at the same time.

I'm pretty sure my Ubuntu partition is /dev/sda3, would that be hd0,3?
deleted - bodhi.zazen's suggestion should work.

---

