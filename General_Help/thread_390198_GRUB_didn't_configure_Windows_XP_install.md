---
title: "GRUB didn't configure Windows XP install"
date: 2007-03-21
forum: General Help
---

### Post by regomodo on 2007-03-21
I've been working at this for at least 6 days. Wiped and formatted main hdds god knows how many times but GRUB refuses to see that i have a windows xp partition.

I have tried editing menu.lst with a guide but it didn't work.
here are the important parts of menu.lst

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

and fdisk -l

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        1275    10241406   83  Linux
/dev/hdc2            1276        1339      514080   82  Linux swap / Solaris

Disk /dev/hdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24321   195358401   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS



/dev/hdc1 is the Ubuntu partition
/dev/sda1 is the XP Pro partition

Any help would be greatly received
Cheers

---

### Post by al7kz on 2007-03-21
grub counts ATA drives first, then SATA, and since XP isn't on the first drive, then you need to remap the drives. Try entering in menu.lst:

title XP
rootnoverify (hd1,0)
map (hd0)(hd1)
map (hd1)(hd0)
makeactive 
chainloader +1
boot

You could also go to a command prompt at the grub menu and enter these commands manually to see if they will boot XP. Start with the rootnoverify command.

---

### Post by regomodo on 2007-03-21
Changed menu.lst by adding that

Rebooted and tried XP

"Error 11 : Unrecognized Device String"

---

### Post by al7kz on 2007-03-21
(hd1,0) is the device string. Apparently grub isn't seeing that drive. Try googling "grub manual"

---

### Post by bulldog on 2007-03-21
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1

Try this one,this should work,at least it works for me.

---

### Post by regomodo on 2007-03-21
Cheers for those hints,I'll try those soon.

At the moment i'm fed up continuously getting things to work with linux so i'm using Acronis OS selector with my SATA drive being the highest priority. Not what i want but i'm miffed off too much to care right now

Now to sort out Americas Army no sound isues and widescreen support in linux. Also nlite windows 2k for my 570e thinkpad, finish some vhdl for my cpld project, respray my motorbike, get a haircut, develop a stash of bw films, resort-out xp install, scan a load of films, releather my tlr, fix my larger carb,get some displays done. F**k me, i should get things done a lot quicker.

Can't wait for the day when i eventually get this install to do what i need it to.

---

### Post by regomodo on 2007-03-21
> **al7kz said:**
> (hd1,0) is the device string. Apparently grub isn't seeing that drive. Try googling "grub manual"

Yeah, i had already done that. It's very long and when i looked in it to find hints, not for long mind you, i gave up.

Well, at least i have a crude dual boot system.

---

### Post by al7kz on 2007-03-21
x

---

### Post by regomodo on 2007-11-19
Sorry to necrobump but Ubuntu has done it again. This time with Kubuntu Gutsy i am left with the same predicament.

Grub has got my setup wrong. I am now left with

>  Error 13: Invalid or Unsupported Executable Format 

my device.map is

```
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
```

and my main bit of menu.lst is

```
 title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=bc3ef77d-44ca-4183-a416-e1f9ed92763e ro 
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=bc3ef77d-44ca-4183-a416-e1f9ed92763e ro single
initrd		/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST
title         Shite
rootnoverify          (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
savedefault
makeactive
chainloader   +1
#
```

Any ideas or pointers?

Cheers

---

