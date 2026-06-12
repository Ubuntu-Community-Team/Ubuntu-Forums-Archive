---
title: "2 operating systems, no grub boot loader. How can I install one?"
date: 2007-10-11
forum: General Help
---

### Post by linuxbun on 2007-10-11
Basically, my originally setup was 2 hard drives (Xp on one, whole disk encrypted 7.04 on the other one). Then the hdd that windows was on screwed up and I replaced it with a Sata HDD (The linux install is on an IDE, not that it should make much difference).

As there is now no bootloader, I can only log into windows and not ubuntu (can't even log into ubuntu even if I temporarily disconnect the windows drive).

I've opened up my encrypted ubuntu disk with: sudo cryptsetup luksOpen /dev/hdb3 tmp then: sudo mount /dev/mapper/tmp /mnt/tmp

And then I went to look @ /mnt/ubuntu/boot/grub/menu.lst

on my encrypted disk to see if I can add the windows drive to it, but after boot folder is just blank. There's no grub in there, So I'm guessing that I need to install it? But I'm unsure how without reinstalling ubuntu, something that I strongly don't want to do.

Any ideas? Surely it can be done without a complete reformat?

---

### Post by Martin Witte on 2007-10-11
here's a descrption on how to do this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

