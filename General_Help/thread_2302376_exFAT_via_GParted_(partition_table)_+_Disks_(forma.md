---
title: "exFAT via GParted (partition table) + Disks (formatting) unrecognized by Windows"
date: 2015-11-09
forum: General Help
---

### Post by jamesisin on 2015-11-09
I have been trying to sort out how to create a partition table and exFAT partition combination using Ubuntu in such a way that Windows will also recognize said exFAT partition.  Thus far I have not succeeded.

I have tried creating partition tables using both GPT and msdos (which I suppose means a MBR) using GParted; then I have tried creating exFAT partitions using Disks (custom partition; specify exfat).

I have both of the exFAT packages installed from the standard repositories and thus am able to create viable exFAT partitions which I have been able to use on multiple Ubuntu systems.

However, if I attach any of these drives to a Windows box Windows asks if I would like to format the drive (which Disk Manager reports as having a RAW partition).

This is the output from fsck on Ubuntu for an example partition:

```
$ sudo fsck.exfat /dev/sdb1
exfatfsck 1.0.1
Checking file system on /dev/sdb1.
File system version           1.0
Sector size                 512 bytes
Cluster size                128 KB
Volume size                2794 GB
Used space                   91 MB
Available space            2794 GB
Totally 0 directories and 0 files.
File system checking finished. No errors found.
```

Something is not right.  Any ideas?

PS:

I have tried creating the exFAT partition from the terminal (using mkfs.exfat /dev/sdX#--which I believe is exactly what Disks does).  Same results.

The two packages which are available in the standard repositories are exfat-utils and exfat-fuse; these are slightly different names for the same packages which used to be in a personal repository.  I do not know who now maintains them.

GParted appears to always present exfat as a greyed-out option (for any user anywhere).  I use it to create a partition table (and possible a blank partition) and then switch to Disks (or the terminal) to create the actual exFAT partition.

---

### Post by sudodus on 2015-11-10
exFAT is a proprietary Microsoft file system. Probably the free tool that you use to create an exFAT file system cannot make systems that are quite compatible with Windows.

The free tools for NTFS and FAT32 are quite old, debugged and polished, but it seems to me, that there are still bugs in the free tools for exFAT.

-o-

***Why*** do you want to made exFAT file systems?

Is it an alternative to

- use Windows to create exFAT file systems?

- create another file system?

---

### Post by jamesisin on 2015-11-10
Yes, of course Microsoft proprietary.  FUSE has a version which is in the Ubuntu repositories.  If this is a bug in FUSE I should want to file a bug report.  Didn't have much luck finding a good place to do that.

FAT is still the only genuinely universal file system.  FAT32 has that awkward 4 GB - 1 byte file size limit, so modern usage really demands exFAT.

In addition to Windows systems not recognizing my Ubuntu-created exFAT partitions, my Oppo BDP-103 (Bluray player) does not recognize them.  It is likely other embedded systems (which license exFAT from MS) will have this same issue.

I'd rather not have to go to a Windows box each time I would like to create an exFAT file system: the FUSE version should work (especially as it is reported that it does work).

---

### Post by jamesisin on 2015-11-10
Mac OSX (10.10 and 10.11) also do not recognize these drives (and asks if I wish to Initialize).

---

### Post by yancek on 2015-11-10
Do you have the exfat software installed in Ubuntu, discussed at the link below.  Various options for different releases so check that.  Some other info on using it on a Mac.

 [http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

---

### Post by jamesisin on 2015-11-10
Yes, those are "both of the exFAT packages installed from the standard repositories".  This allows me to make filesystems which purport to be exFAT but which prove to be exFAT only if you are using another Ubuntu system.

---

### Post by sudodus on 2015-11-11
Have you considered the [UDF](https://en.wikipedia.org/wiki/Universal_Disk_Format) file system?

[http://tanguy.ortolo.eu/blog/article93/usb-udf](http://tanguy.ortolo.eu/blog/article93/usb-udf)

> Good news: there is one file system that is implemented almost everywhere as well, and which does not suffer from such limitations. UDF, the Universal Disk Format, is an ISO standard originally designed for DVDs, but it is perfectly usable for USB sticks. It also supports POSIX permissions, with one killer feature for removable media: a file can belong to no specific person or group.

So, to use it, assuming you USB stick is /dev/sdc:

```
$ dd if=/dev/zero of=/dev/sdc bs=1M count=1
$ mkudffs -b 512 --media-type=hd /dev/sdc
```



---

### Post by gedakc on 2015-11-11
Depending upon how you created the partition, it is possible that there is problem with the partition type code that Windows is expecting.

You might try first creating the partition in GParted as fat32, then from the command line formatting the partition to exfat.

---

### Post by jamesisin on 2015-11-11
Ok, gedakc, I have run some tests for your theory.

I tried both msdos (MBR) and GPT with the same results.  I created the partition table in GParted and then formatted the drive with FAT32.  I then switched to Disks (or the terminal) and re-formatted the drive in exFAT.

After this GParted reports that partition as "exfat", Disks reports it as "Partition Type: W95 FAT32 (LBA)" and "Contents: exFAT (version 1.0)", df -T reports it as "fuseblk", and blkid reports it as "exfat".  Regardless, the Mac still wants to "Initialize" my drive.

It was a good guess but still no luck.

sudodus - An interesting prospect.  I'll look into that file system.  Not sure it would be the best choice here at work though.

I'm still up for filing a bug report if anyone knows where I might do that for FUSE.

---

### Post by jamesisin on 2015-11-11
Actually, sudodus, your suggestion lead to a discovery.

Formatting the drive using your method gave me a drive without a partition table but with a file system (UDF).  This worked on all three formats (though GParted didn't like it; more on that in a moment).  Then I thought why not try replacing the file system (as I had been doing with FAT32 and exFAT previously).  This gave me a drive without a partition table with with a different file system: exFAT.  This also worked on all three formats.

GParted, however, does not care for this at all.  It reports that drive as "unallocated" as it did when I formatted it with UDF.  So it appears that we have narrowed the problem somewhat.

---

### Post by sudodus on 2015-11-12
That's interesting. So 'your' exfat was accepted by Windows when created directly on the device (without any partition). I wonder if it made a difference that udf had been there and maybe left some trace, or if the wiping procedure (overwriting with zeros) made the difference.

---

### Post by jamesisin on 2015-11-12
There is no partition table.  That's the difference.  Of course this is an apparent problem for GParted.  It's a little weird for me too.  Still hoping someone will stop in and point me to a bug reporting location.

---

### Post by sudodus on 2015-11-12
Not the only difference.

Using the file system without a partition is the old 'floppy disk way'. I think you would succeed with udf also in a partition (if I rememeber correctly, I tried that some months ago).

---

### Post by jamesisin on 2015-11-12
Yes, that was my test exactly.  I created the drive UDF per your instructions (which zero the drive and create no subsequent partition table).  Then I used Disks to format the UDF into exFAT.

---

