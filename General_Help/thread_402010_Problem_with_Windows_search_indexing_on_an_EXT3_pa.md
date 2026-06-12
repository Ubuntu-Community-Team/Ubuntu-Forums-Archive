---
title: "Problem with Windows search indexing on an EXT3 partition"
date: 2007-04-05
forum: General Help
---

### Post by 50words on 2007-04-05
I am dual-booting Windows XP and Ubuntu, and using a separate partition (H:) for my /home directory in Ubuntu and my "My Documents" directory in Windows. It is formatted as an EXT3 partition, and I am using FS Driver in Windows.

I am having trouble with indexed search programs like Google Desktop and Windows Desktop Search in Windows, however. Neither seems to want to index the contents of my home/My Documents directory. This is a big problem when indexed search has pretty much become a necessary, everyday part of my computing.

(Incidentally, I had the same problem trying to use online backup programs like Carbonite and Mozy.)

I know this is more of a Windows question than a strictly Ubuntu question. Will I have to convert the partition to FAT32 (oh God no) so that both operating systems can use it? Will Feisty support NTFS read and write? What would you suggest?

---

### Post by computerwiz3491 on 2007-04-05
There is always NTFS-3g to get Ubuntu to read-write to NTFS. As far as reading ext3 from Windows, I have used FS Driver with no problems.

---

### Post by 50words on 2007-04-05
I just found out about NTFS-3g, actually. I'll give that a try, as I need functionality in Windows more than in Ubuntu. I guess that way I'll find out if the problem is related to file system or just partitioning.

---

### Post by GuitarRocker2562 on 2007-04-05
try this command to get your ntfs partiton readable and writeable "sudo apt-get install ntfs-config" this porgram is a little gui that makes setting up your ntfs partition supper easy!

---

### Post by 50words on 2007-04-09
> **GuitarRocker2562 said:**
> try this command to get your ntfs partiton readable and writeable "sudo apt-get install ntfs-config" this porgram is a little gui that makes setting up your ntfs partition supper easy!

Thanks. I've decided just to change my /home directory to NTFS, since I need Windows Desktop Search to work more than I need Ubuntu.

---

