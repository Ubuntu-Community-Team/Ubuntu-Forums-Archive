---
title: "update-grub pains"
date: 2007-06-03
forum: General Help
---

### Post by seamuso on 2007-06-03
Grub counts drives strangely when you have a mix of pata / sata .. In such, both hda1 and sda1 become root(hd0,0) No big issue there and easy to workaround. The problem I've run into is that everytime I cahnge anythin that requires an update-grub I end up with my sda1 listing as root(hd2,0) in my menu.lst (all entries get updated to this).

kopt-= is pointed to sda1 and groot= has been set to hd0,0
menu.lst```

# kopt=root=UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)
```fstab```

# /dev/sda1
UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 /               ext3    defaults,errors=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0 1
```but regardless, this is what I get everytime update-grub is run```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 ro single rootflags=data=writeback
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-386
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=d55ca51d-4e5e-4607-a638-6e85cd81c5d2 ro single rootflags=data=writeback
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```is there anything else I can change to force update-grub to correctly set my root to hd0,0?

---

