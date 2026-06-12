---
title: "MBR screwed, totally starting over"
date: 2007-03-30
forum: General Help
---

### Post by grsing on 2007-03-30
So, my Edgy install was messed up, Feisty Beta got screwed up, and my Windows install has been screwed up for a long time now; that means it's time to start over (and it gives me a chance to reduce the size of my Windows install, yay). So, I'd been having problems with grub/mbr for a while (had to just use the live CD and select the option to boot from first hard disk). Now, both my hard disks are formatted, completely blank, but the problem persists (if I install Windows or Feisty, I still get the error "Error locating operating system." I made a windows restore floppy, but the command fdisk /mbr doesn't seem to work, just gets me a "Bad command or file name." I tried using the automated restore MBR on the XP CD, only changed the error I got from "Error locating OS" to "Error locating operating system." There's no data on the disks now (it's all backed up on externals, which are currently disconnected from the system to make sure I don't have a brain fart and really start hating myself), so what is the best way to just return the MBR back to whatever it originally came from and start over with installing Windows and Feisty? Sorry for the long post, just wanted to make sure it's clear.

---

### Post by grsing on 2007-03-30
OK, retried the Windows MBR restore thing, and redeleted all my partitions, and now the Windows install seems to be proceding after the restart, so it may be fixed. Just have to wait the friggin 39 minutes it takes XP to install (oh, how I love Ubuntu compared to Windows, too bad I can't quite go Windowsless). I'll update if it somehow refails.

---

### Post by bravemosquito on 2007-03-31
Which version of GRUB you use?

---

