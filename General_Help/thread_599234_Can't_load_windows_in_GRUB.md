---
title: "Can't load windows in GRUB"
date: 2007-11-01
forum: General Help
---

### Post by joebanana on 2007-11-01
Hi I installed first 7.10 then windows cuz my ATI tvout doesn't wok on Ubuntu. Windows were working. Then I reconfigured GRUB and add windows entry in it. But if I choose windows at boot time in GRUB menu it just writes "Starting up..." and nothing happens.

sudo fdisk -l:

```

Disk /dev/hda: 81.9 GB, 81964302336 bajtov
255 heads, 63 sectors/track, 9964 cylinders
Units = steze of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95099509

  Naprava Zagon    Za&#269;etek       Konec     Bloki    Id  Sistem
/dev/hda1               1        2067    16603146   83  Linux
/dev/hda2            2068        2191      996030   82  Linux izmenjalni / Solaris
/dev/hda3            2192        7662    43945807+   b  W95 FAT32
/dev/hda4   *        7663        9964    18490815    b  W95 FAT32

```

I have windows on hda4 and Ubuntu on hda1
sudo gedit /boot/grub/menu.lst(part that might be usefull):

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=da5004a7-2967-4ed5-9dfe-b319fd630cd1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=da5004a7-2967-4ed5-9dfe-b319fd630cd1 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows
root		(hd0,3)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Saubazi on 2007-11-01
You sure your windows isn't /dev/hda3 ? -> (hd0,2) since you have also that partition?

The windows stuff also rings a bell somehow but  I think there is an issue if the windows is
not on first harddisk (if it was some /dev/hdb or so or even on a SATA drive if you have IDE drives
present in system) - then you'd need to use map option on grub but in your case I think it should work
like that - except you might try that different partition option...

---

### Post by joebanana on 2007-11-01
Yes, I am sure it's on hda4:

```

rok@rok-desktop:/media/hda4$ ls
Documents and Settings                         pagefile.sys
found.000                                      Program Files
hiberfil.sys                                   System Volume Information
mmcInst.log                                    windows

```

I also have just one IDE drive

---

### Post by Saubazi on 2007-11-01
Don't know about that - which windows is it? 98 used to make a separate boot partition or something like that (although I think your hda3 looks bigger than such) - Don't take my word for it but I think there's no harm trying other options... At least according to this  [http://wiki.ubuntuusers.de/GRUB](http://wiki.ubuntuusers.de/GRUB)

---

### Post by joebanana on 2007-11-01
It's windows XP profesional SP2 or something like that

---

### Post by Saubazi on 2007-11-01
Ok anyway I do not know your configuration and what is the purpose and story behind the /dev/hda3 but it might be worth a try to input (hd0,2) on grub and see what happens - there should be no harm trying, at least I have inaccidently had those entries wrong often enough...Other than that I can't figure out why it should not work - your grub entry seems "grammatically" correct to me...

---

