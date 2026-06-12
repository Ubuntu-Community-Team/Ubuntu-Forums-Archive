---
title: "Ubuntu 15.04, grub sollowed it's tounge."
date: 2015-09-09
forum: General Help
---

### Post by william_estrada on 2015-09-09
Hi group,

  My new install of Ubuntu 15.04 has been running for about a month.  For some undetermined reason
grub stopped working, LIFO came up at boot time.  When I tried the reinstall grub, I got this error:```
/dev/sda does have any corresponding bios 
```It turns out that the some grub support files in /boot/grub where missing. After reinstalling grub and grub2, I got grub-install to work with:```

grub-mkconfig > /boot/grub/grub.cfg
mount /dev/sda/mnt
grub-install --root-directory=/mnt /dev/sda
```The process was not complete.  Grub is now using menu.lst instead of grub.cfg.  Grub-install still does not work with the standard command line.
```
grub-install /dev/sda
```

I would like to get grub back to the install state.  Any pointers?

Thanks for your time.

---

### Post by NathanRodriguez on 2015-09-09
Have you tried the boot repair with the install media?

---

### Post by oldfred on 2015-09-09
If you go menu.lst that is grub legacy not grub2.
You can run a full uninstall/reinstall of grub from Boot-Repair or manually to restore grub2.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you can boot into your install, then you can skip the chroot. That is for using live installer to work on install.

 chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

