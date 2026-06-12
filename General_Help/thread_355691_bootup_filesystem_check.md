---
title: "bootup filesystem check"
date: 2007-02-07
forum: General Help
---

### Post by n_hendrick on 2007-02-07
okay you know that screen that pops up on boot if you have an error on your filesystem during the filesystem check and it gives you to options hit control-d or enter root password. Well I just resized my root partition and I keep getting that error on boot, but the error is for my hda device not my hdb device.....heres the error:

There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:00/01, 425:53/4e

I hit control-d and boot into linux, and run fsck on hda2 and I get the following options to restore the boot sector.....

1) Copy original to backup
2) Copy backup to original
3) No action

No matter what I do I can't get this error message to quit poping up. I don't know how I messed up my windows drive when I was resizing my linux drive but I did and I'm totally lost at what to do next to fix the problem.

---

### Post by n_hendrick on 2007-02-07
I don't know what I did but its working now.......go figure

---

