---
title: "dual boot not going smoothly..."
date: 2008-01-09
forum: General Help
---

### Post by little brad on 2008-01-09
hhhokay.

first of all let me say i had a dual boot of XP and ubuntu 7.10 a few months back. long story short, my drive got trashed and i had to start over.

i've got 3 internal 120gb drives. disk 0 is partitioned into 3.

partition 1 - NTFS - windows XP. it's running fine.

partition 2 - ext3 - has kubuntu installed. mount point is '/'

partition 3 - swap

i used the kubuntu live cd to create/format the ext3 and swap partitions. after installation and reboot, it went directly into windows as if kubuntu wasn't there at all.

i booted into system rescue CD and ran gparted. changed the boot flag from the windows partition to the linux one. reboot and get 'error loading operating system'.

where to from here? thanks in advance.

---

### Post by little brad on 2008-01-09
i was reading that linux requires 2 entries on the MBR, and one of my drives was flagged to boot that didnt need to be, but... even after removing that flag, no dice :-(

---

### Post by amdalex on 2008-01-09
Have you tried to edit Grub? On my computer I had Ubuntu insatlled on the master IDE drive and then edited the Grub file and added a windows 98 entry for the slave drive. It works like a charm.

---

