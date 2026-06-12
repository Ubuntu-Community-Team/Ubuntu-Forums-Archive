---
title: "Grub &amp; link loading with 4 HDD's"
date: 2008-04-30
forum: General Help
---

### Post by oygle on 2008-04-30
Have been able to run Ubuntu 7.10 sucessfully on a computer, that has 2 hard drives, default grub boot is Ubuntu, and the other boot (to the other physical drive) is to Windows 95b. See [Grub & link loading with 2 HDD's]("http://ubuntuforums.org/showthread.php?t=577185")

Current device.map

```

(hd0)	/dev/sda
(hd1)   /dev/sdb

```

and the last part of menu.lst

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3597ebdc-48ba-4c14-b8ae-78646573b656 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3597ebdc-48ba-4c14-b8ae-78646573b656 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows 95
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

```

Both these hard drives are ATA. Now, I'd like to place these 2 ATA drives on another computer (one that has a lot more grunt). The other computer has XP Pro on it, and one SATA drive. I'd prefer to 'update' to the new version of Ubuntu with a new install, by putting it on a new SATA drive. Basically, the computer would have 4 hard drives (2 SATA and 2 ATA), as follows:

device.map
```

(hd0)	/dev/sda
(hd1)   /dev/sdb
(hd2)	/dev/sdc
(hd3)   /dev/sdd

```

hd0  -  Ubuntu 8.04
hd1  -  Win XP Pro
hd2  -  Win 95b
hd3  -  Ubuntu 7.10

Would the very last part of menu.lst be something like this ..

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft XP Pro
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows 95
map             (hd0) (hd2)
map             (hd2) (hd0)
root            (hd2,0)
savedefault
makeactive
chainloader   +1

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Ubuntu 7.10
map             (hd0) (hd3)
map             (hd3) (hd0)
root            (hd3,0)
savedefault
makeactive
chainloader   +1

```

I may not actually have any need to boot to Ubuntu 7.10, as after all the necessary data files have been copied to the 8.04 drive, then I may reformat it, and use it just for data storage, or partition it up, and have some of it for swap.

Does this all look okay ? As they are all seperate physical drives, I see no reason why there would be problems ?

When I boot to 8.04, I should be able to see all other drives, and when I boot to either XP or win95b, I can only ever access the other Win drive (which is what I want).

Thanks !!

---

### Post by oygle on 2008-05-02
Can this be done by the method I have described ??

---

