---
title: "Remove the quiet-line (after the initrd-line, not quiet splash) in grub menu.lst."
date: 2007-10-19
forum: General Help
---

### Post by flagel on 2007-10-19
This is a paste from a standard GRUB menu.lst:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/hda6_crypt ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

Now, you cannot edit these lines in an regular texteditor because update-grub will overwrite them. The "quiet splash" on line 3 can be removed with the help of changeing "# defoptions= queit splash" to "# defoptions=". But how does one remove "quiet" on line 5? This is most important since otherwise you will not be prompted about passwords for encrypted partitions and therefore not be able to boot into Ubuntu.

Thanks in advance!

---

### Post by stacktracer on 2008-03-17
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/137136](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/137136)

---

