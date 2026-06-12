---
title: "Why did my SD card just become &quot;read only&quot;?"
date: 2008-03-09
forum: General Help
---

### Post by mivo on 2008-03-09
I used my MiniSD memory card a few times today to store data, and it suddenly, for no apparent reason. got mounted as "read only". I used an USB adapter, but after rebooting I also tried it with a SD adapter in an USB card reader. It worked before, but without me doing anything, I can't write files to the device anymore (not even as root).

The permissions look strange, too. The user is the owner and can create and delete files (no, I cannot). The group is root, and has no rights, and others also have no rights. What may have this been caused by? I made no changes whatsoever, and it worked all day before. Also, how do I fix this? I need to copy files on that memory card.

---

### Post by mivo on 2008-03-09
I fixed this problem by backing up the data on the SD card and then formatting it with GParted. After that, it worked fine again. I still have no idea how it got messed up, though. This is the type of possible bug that's really problematic in a professional environment.

---

### Post by prshah on 2008-03-09
run fsck on it to check for errors... is it set as FAT?

Also, safe-unplug your usb device / mini sd card, wait a couple of seconds, then plug it back in. then open a terminal and post the output of "dmesg | tail -10"

Cheers,
PRShah

---

### Post by barbedsaber on 2008-03-09
might be worth double checking if there is a little tab that you can move (on the sd card) and if there is, to make sure it not in the locked position. you would be surprised how often tthis sort of thing happens, I had spent hours trying to set up my wifi, only to find the little wireless switch at the front of my lappy was off, hehe, must have bumped it. :)

---

