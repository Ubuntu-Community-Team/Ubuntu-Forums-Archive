---
title: "[SOLVED] update-grub labeling kernels wrong in menu.lst"
date: 2008-05-02
forum: General Help
---

### Post by Zorael on 2008-05-02
As the topic implies. I toyed around in the grub utility to refresh my memory of how to restore grub, and now when I update-grub it labels my Ubuntu kernels (from the repositories) as merely Debian kernels.

```
title           Debian GNU/Linux, kernel 2.6.24-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/sdb2 ro quiet splash vga=792 resume=/dev/sdb4
initrd          /boot/initrd.img-2.6.24-16-generic
boot

title           Debian GNU/Linux, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=/dev/sdb2 ro single
initrd          /boot/initrd.img-2.6.24-16-generic
boot
```

Instead of, as it should look:
```
title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f0ad0401-9645-4dad-ae3e-289a6b34f37c ro quiet splash vga=792 resume=/dev/sdb4
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f0ad0401-9645-4dad-ae3e-289a6b34f37c ro single
initrd          /boot/initrd.img-2.6.24-16-generic
```


Where did I mess up? :(

---

### Post by Zorael on 2008-05-02
Might be worth mentioning, but I don't have the grub available in the repositories installed, rather opting for a version of grub-gfxboot I found linked to here on the forums.

```
zorael@sunspire:/boot/grub$ dpkg -l grub-gfxboot grub
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                                         Version                                      Description
+++-============================================-============================================-========================================================================================================
ic  grub                                         0.97-29ubuntu21                              GRand Unified Bootloader
ii  grub-gfxboot                                 0.97-5                                       GRand Unified Bootloader
```

Mentioned forum post: [http://ubuntuforums.org/showthread.php?t=481957](http://ubuntuforums.org/showthread.php?t=481957)
The amd64 version didn't work for me, but forcing architecture got me the i386 version running.

---

### Post by Zorael on 2008-05-02
Nevermind, the culprit was apparently grub-gfxboot. So I'll just have to do a switcheroo every time I update kernels.
```
$ sudo su
# dpkg --purge grub-gfxboot
# aptitude install grub
# update-grub
# aptitude purge grub
# dpkg -i --force-architecture grub-gfxboot_0.97-5_i386.deb
```

---

