---
title: "Gparted, fat32, no access to disk"
date: 2008-04-18
forum: General Help
---

### Post by OiPenguin on 2008-04-18
I'm using Simple Backup Suite to back up my laptop to my server and my server to an external disk. I'm very pleased with Simple backup suite, however I've realised that the backup to the external disk never exceeds 4 GB. It suddenly struck my that that's FAT32's limitation.

Problem 1
Is it possible to convert from Fat32 to any other format (which is recommended) without loosing the data?

Problem 2
I'm accessing the server with NX Remote client and I'm logged in as a regular user (not root) on the server. When starting gparted, I've not got access (padlocked) to any format options for neither of my three disks. Starting gparted with 'sudo gparted' makes no difference. How do I get priveliges to format the disks?

Yours,

Lars

Simple Backup Suite: [http://sourceforge.net/projects/sbackup/](http://sourceforge.net/projects/sbackup/)

---

### Post by zvacet on 2008-04-18
1.No,because formating means lose of data.
2.I don´t know.

---

