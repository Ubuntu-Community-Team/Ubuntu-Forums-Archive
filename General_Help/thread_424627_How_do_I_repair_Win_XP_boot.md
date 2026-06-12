---
title: "How do I repair Win XP boot?"
date: 2007-04-26
forum: General Help
---

### Post by OMRebel on 2007-04-26
Hey everyone.  I dual boot Ubuntu and Win XP.  However, after doing a fresh install of Ubuntu on my hd0 drive, I cannot boot into Windows now (on the hd1 drive).  All i get is "Starting up" on the screen after selecting Windows off of the Grub menu.  What's the best way to fix the Win boot without messing up Grub?

Thanks.

---

### Post by hardyn on 2007-04-26
I really dont think windows likes being on drives that arn't hd0,  I have not had this troube myself, but if i were to hazard a guess i would think you would have to add something like this to your /boot/grub/menu.lst file:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```

notice hd1,0 as opposed to hd0,0

as i have not had to fix this problem myself, this suggestion comes with no warranty.

---

### Post by confused57 on 2007-04-26
> **OMRebel said:**
> Hey everyone.  I dual boot Ubuntu and Win XP.  However, after doing a fresh install of Ubuntu on my hd0 drive, I cannot boot into Windows now (on the hd1 drive).  All i get is "Starting up" on the screen after selecting Windows off of the Grub menu.  What's the best way to fix the Win boot without messing up Grub?

Thanks.

You'll need to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and

```
gedit /boot/grub/menu.lst
```

this should enable you or someone else to determine the correct Window's entry.

Added: You would need map commands for Windows on a 2nd hd:
map  (hd0) (hd1)
map  (hd1) (hd0)

---

### Post by OMRebel on 2007-04-26
Doh!  Just saw in my previous post where I switched up hd0 and hd1 when making the post.  Sorry about that.  Ubuntu is on hd1 and Win on hd0.

sudo fdisk -l:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS
brad@brad-desktop:~$ 


menu.lst:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=edef80a2-60f5-4278-92bc-ebe35f9c7277 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=edef80a2-60f5-4278-92bc-ebe35f9c7277 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

The problem isn't really with Grub, but with the Windows bootloader itself now (I believe).  Previously, I was running Edgy, and did a clean install of Fiesty.  Apparenlty, it got a bit too Fiesty...lol

---

### Post by confused57 on 2007-04-26
Since Windows is on the (hd0) drive, you can take out the map commands:
```
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```

Hopefully, this will work if your Window's bootloader is OK.

---

