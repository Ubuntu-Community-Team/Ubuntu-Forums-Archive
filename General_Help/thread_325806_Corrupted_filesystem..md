---
title: "Corrupted filesystem."
date: 2006-12-26
forum: General Help
---

### Post by Rizado on 2006-12-26
Hi!

I have a drive that have begun to act strangely. It all began when I was playing with hdparm. Partitions dissapered then mysteriously reappered again, some files is corrupted and copying is sometimes extremely slow (2-3 MB/s). :neutral: 

I've moved the drive to my main computer and right now I'm trying to save what can be saved. I started by mounting partitions and to my surprise it worked! I thought I had lost everything. I started making backups and at start it worked great. A few files was corrupted but nothing bad.
Copying speed were at about 50mb/s and the first 40gb or so went great. But when I tried to copy my games it was just dead slow. I cancelled and moved on to copy some config files instead , afraid the drive was about to die. It didn't work out so I unmounted and right now I'm running e2fsck on the partitions. It says they have errors and -p doesn't work. It say I have to run manually ](*,)

```
sudo fsck.ext3 -v /dev/hda3
e2fsck 1.39 (29-May-2006)
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 858370 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 338785.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 338785, i_blocks is 304, should be 104.  Fix<y>? yes

Error reading block 2002518 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 555906.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 555906, i_blocks is 272, should be 104.  Fix<y>? yes

Error reading block 1380138 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 674036.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 674036, i_blocks is 552, should be 104.  Fix<y>? yes

Error reading block 1730765 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 852571.  Ignore error<y>? yes

Force rewrite<y>? yes

Inode 852571, i_blocks is 144, should be 104.  Fix<y>? yes
``` These are some lovely errors I have. Some yes or no answers, kinda easy but the thing is I have no idea what I'm doing :-? Am I making things worse by answering yes? Also it is horribly slow. This is a 10gb partition and I just can't do this with a 100gb one...

---

### Post by wpshooter on 2006-12-26
First I hope you have some backups of the data on these drive(s) but it does not sound like you do.

Second, unless this information is some kind of vital business related info, I would WIPE these drives clean and then put them back in the machine and get the hard drive manufacturers diagnostic software and check them to see if the have any mechanical problems.  It could be that they are O.K. physically and that your data has just been scrambled by the use of a poorly written hard drive utility.

Good luck.

---

### Post by Rizado on 2006-12-26
You're absolutely right, I don't have any backups :p 
It's not anything important really, just my old installation. I've installed edgy on a new raid array since it's a new installation I'd like som scripts and configs I've made. I have backups on the important stuff and managed to copy my music and such things.

I'm gonna follow your advice and wipe it because this is way to slow.

I just checked S.M.A.R.T with smartctl. The result isn't very good.
```
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.
```
Hahaha, well I wasn't that surprised because it's kinda old and is making some noise. Luckely I've just recently bought new drives!

---

