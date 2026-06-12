---
title: "Luks corrupt?"
date: 2013-09-13
forum: General Help
---

### Post by linuxuser21 on 2013-09-13
Being that this is my first expierience with encryption, I'm not quite sure where to begin with this; however, I am suspecting some hard drive corruption is involved.
I have files on a 20gb Luks ext4 partition (sda6) that I created a while back.  Shortly after I created this partition, previously active folders suddenly started coming up empty.  Still being able to access most of the files, I created new folders and began replacing & recreating the missing data.  Upon adding files to these folders, THEY started coming up empty.
Some files are unable to open & when I try to copy them I get I/O errors.
I recognize the I/O errors (and could possibly be attributed to a bad copy & paste); but, are the empty folders signs of corruption and is there any chance of recovering the data?
I've followed [this]("http://blog.miketoscano.com/?p=72") guide; but, are coming up with errors left and right.

fdisk:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001fa89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048       43007       20480   83  Linux
/dev/sda2           45054   976773119   488364033    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5           45056     4141055     2048000   82  Linux swap / Solaris
/dev/sda6       935813120   976773119    20480000   83  Linux
/dev/sda7         4143104    45103103    20480000   83  Linux
/dev/sda8        45105152    86065151    20480000   83  Linux
/dev/sda9        86067200   127027199    20480000   83  Linux
/dev/sda10      127029248   935811071   404390912   83  Linux

```

---

### Post by sudodus on 2013-09-14
I would backup everything valuable and start from the beginning with the drive.

- check the S.M.A.R.T. status

- when booted from another drive, check the file system for errors

```
sudo e2fsck -f /dev/sdxy
``` where x is the drive letter and y is the partition number.

- if the drive is bad (more than a few bad sectors), you should get another one, because it is probably starting to crash.

- make a new file system or rather, I suggest you start by installing an encrypted Xubuntu or Lubuntu system with

a. encrypted home (as offered in the installer)

b. encrypted home and disk (double encryption), according to this instruction (yes, I know it is instructions for testing, but it really helps creating a good encrypted system (and you should be able to use the instructions also with a released system)

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

I used it to test Lubuntu Saucy alpha2 and beta1 recently, and I could make systems that work.

---

### Post by linuxuser21 on 2013-09-28
Well, according to [this]("http://ubuntuforums.org/showthread.php?t=1845982"), it does look like the hard drive is failing/corrupt.  Like I said, I'm used to I/O errors; but, not so much folders suddenly coming up empty.  Still looking for a way to recover data; fsck isn't cooperating; so, looking elsewhere for a solution.

---

