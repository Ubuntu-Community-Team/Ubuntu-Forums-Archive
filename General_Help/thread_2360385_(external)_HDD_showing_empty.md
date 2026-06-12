---
title: "(external) HDD showing empty"
date: 2017-05-04
forum: General Help
---

### Post by random411 on 2017-05-04
So, this happened about 1,5 years ago. It was in fact the main HDD of my old Ubuntu machine, and it ran fine until one day there was a problem with the power supply unit. Changed the faulty thing and then suddenly could not boot the system any more: Boot sequence failure.

Later, I got a docking station, took the HDD out if the old machine and plugged it in. It is recognized but shows as empty, save for the System Volume Information folder. The Properties tab also says "39 MB of 39 free", "2 files, 0 KB in total". Tried this with my current Ubuntu machine and with another Win machine, with the same result.

How on Earth could this be and where are my files? And most important, can they be recovered and how? I had a backup of the most essential stuff, but not of all of it. There is a couple files that I absolutely cannot lose, and that were not backed up yet.

Thanks for any help!!

---

### Post by Bashing-om on 2017-05-04
random411; Hello; Welcome to the forum .

How about try'n to spare off the super block to get a valid partition table for the drive ?
See: [http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

[INDENT][INDENT]maybe YeS
[/INDENT][/INDENT]

---

### Post by random411 on 2017-05-07
Thanks :)

sudo fdisk -l
gave me the following:
Medium /dev/sdc: 38,3 GiB, 41110142976 Bytes, 80293248 Sektoren
Einheiten: sectors von 1 * 512 = 512 Bytes
Sektorengröße (logisch/physisch): 512 Bytes / 512 Bytes
I/O Größe (minimal/optimal): 512 Bytes / 512 Bytes
Typ der Medienbezeichnung: dos
Medienkennung: 0xf2415877

Gerät      Boot Start     Ende Sektoren Größe Id Typ
/dev/sdc1          63 80276804 80276742 38,3G  7 HPFS/NTFS/exFAT

And 
sudo fsck.ext4 -v /dev/sdc1
gave me:
e2fsck 1.42.13 (17-May-2015)
/dev/sdc1 ist eingehängt.
e2fsck: Fortsetzung nicht möglich, wird abgebrochen.

That means literally, that sdc1 is mounted, but the process (e2fsck) cannot continue and will be terminated.


Obviously it is not the superblock that causes the problem.

---

### Post by yancek on 2017-05-07
> /dev/sdc1          63 80276804 80276742 38,3G  7 HPFS/NTFS/exFAT

Your fdisk output above for sdc1 clearly shows that is a windows ntfs filesystem.  The fsck ext4 command you show you ran was on sdc1 which is an ntfs filesystem and that won't work.  fsck only works on Linux filesystems, you need to run chkdsk from windows on sdc1.  Do you have the right drive/partition.

---

