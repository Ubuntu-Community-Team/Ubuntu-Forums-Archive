---
title: "GRUB Booting stage 1.5 Error 15?"
date: 2007-06-13
forum: General Help
---

### Post by crazy_vyper on 2007-06-13
Hi guys, trying to load up my laptop which (was) dual booting Ubuntu Feisty and WinXP.

The problem:
Can't load past the boot loader. I get the messages;
GRUB Loading Stage1.5.


GRUB loading, please wait...
Error 15

I Can't do anything except CTRL+ALT+DEL to reboot the computer. I can't access any terminal to try fix grub, and nothing has worked. As far as i know, i can't boot past GRUB into any "dos" like booting.

Any help appreciated, thanks...

---

### Post by logos34 on 2007-06-13
You might want to take a look at [this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15")

You'll need to download the SuperGrub iso and burn it to a disc.

It couldn't hurt to boot from the ubuntu live or alternate install CD and do a filesystem check of / :
sudo fsck /dev/hdax    x = your root partition #  (or sdax if sata drive)

---

