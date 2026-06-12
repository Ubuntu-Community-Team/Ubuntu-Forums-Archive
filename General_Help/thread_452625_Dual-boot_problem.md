---
title: "Dual-boot problem"
date: 2007-05-23
forum: General Help
---

### Post by rob_w on 2007-05-23
I installed Ubuntu on a 30Gb partition of a clean hard drive about a month ago, and then the other day installed XP in the remaining 50Gb. Having enjoyed Ubuntu's simplicity, I foolishly assumed that this would 'just work', but instead I can now only boot into XP. No GRUB screen to choose what to boot pops up at all, and XP's disk manager seems to say that the partition is active. Any suggestions?

---

### Post by ngdias on 2007-05-23
I once solved it by using the 'alternate' CD install. There is an option there that allows you to run grub again. You should also check some grub documentation/tips on adding an Windows booting option on a grub menu.

---

### Post by merlinus on 2007-05-23
You can reinstall grub by booting from the Ubuntu live cd (or any other).  When up-and-running, open a terminal and enter these commands, one at a time, being sure to write down the results of find.  Then change what I have given to whatever your results are.

```

sudo grub
find boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

```

You may then have to add lines similar to what I have given below to etc/boot/grub/menu.lst.  Add these after all of the linux kernel entries.  The most important change will be to the root entry.

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Good luck!

-merlin

---

### Post by rob_w on 2007-05-23
Cheers for the help. I'll give it a go tomorrow.

---

### Post by merlinus on 2007-05-23
BTW, the root in grub is NOT the same as the root in menu.lst.  In the example I gave, root (hd0,0) in menu.lst means that windows is installed in the first partition on my one and only hard disk.

The root in grub (hd0, 7) means that grub lives in partition no. 7 (ubuntu's numbering) of my hard disk.

-merlin

---

### Post by dnstalford on 2007-05-28
I'm afraid I'm a bit of a NOOB, but I've just sorted out a very similar problem, very easily after trolling the various support forums.  Just installed an old copy of XP to play some of my games on, and had to fix GRUB.

Found a program called SUPER GRUB DISK that when written to CD/floppy is used to automatically fix your MBR/GRUB.  Dead handy - will be keeping it around for those times when I mess up!

---

