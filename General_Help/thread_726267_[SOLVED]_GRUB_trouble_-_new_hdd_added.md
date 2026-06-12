---
title: "[SOLVED] GRUB trouble - new hdd added"
date: 2008-03-16
forum: General Help
---

### Post by HumbleGod on 2008-03-16
Hello....I added a new 500GB SATA hard drive to complement my existing SATA drive (with Windows) and my PATA drive (with Ubuntu 7.04). Oddly, when I added the new drive, the existing Windows drive was changed in my system from SDA to SDB, and my new drive became SDA. This led to some brief trouble and some need to edit my fstab, but otherwise things work fine.

Unfortunately, while GRUB (on HD0) still lists my Windows XP boot as an option, when I select it it freaks out and won't boot Windows. I assume this is due to the assignment change from SDA to SDB, but I don't know much about editing my menu.lst. Can anyone give me any advice on what changes I need to make to my menu.lst so that it recognizes the correct partition as my Windows one?

Here's my current menu.lst, with some comments removed for clarity and brevity. The Windows entry is at the end:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

default		0

timeout		10

### BEGIN AUTOMAGIC KERNELS LIST
## ## Start Default Options ##
# kopt=root=UUID=5dd154c3-888c-4ca8-8390-283df8ffd930 ro
# crashdump=0
# groot=(hd0,1)
# alternative=true
# lockalternative=false
# defoptions=quiet splash
# lockold=false
# xenhopt=
# xenkopt=console=tty0
# altoptions=(recovery mode) single
# howmany=all
# memtest86=true
# updatedefaultentry=false
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5dd154c3-888c-4ca8-8390-283df8ffd930 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5dd154c3-888c-4ca8-8390-283df8ffd930 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5dd154c3-888c-4ca8-8390-283df8ffd930 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5dd154c3-888c-4ca8-8390-283df8ffd930 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by scragar on 2008-03-16
I'm guessing that windows has just been moved from hd1 to hd2, so that little edit at the end should work:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1
```

---

### Post by HumbleGod on 2008-03-16
That did the trick. Thanks!

---

