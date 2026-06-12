---
title: "df -h self-inconsistent: used + avail != size"
date: 2013-11-12
forum: General Help
---

### Post by meta_qoph on 2013-11-12
I have a brand new Ubuntu install; the first thing I did was open a terminal to verify my partition sizes, and I found:

```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       825G  106M  783G   1% /home

```

So, I seem to missing 42 GB? I checked a few other ways:

```

~$ df -v
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda6      864982632  108444 820912540   1% /home
~$ du -sh /home
47M    /home

```
Almost all of the size reported by du is due to .mozilla and .cache.

I then installed gparted, which says that /dev/sda6 is 839.19 GiB, with  13.39 GiB (2%) used, and 824.80 Gib (98%) unused. (It is formatted as  ext4, if that matters.) So, how do I find out how much space is being used on my /home partition? And if it really is 13 or 42 GB, how do I free up that space?

Thanks!

---

### Post by oldfred on 2013-11-12
You have at least three things that may be different and different tools may report including or not including that data.
GiB vs GB, reserved space, space used by formatting by journal. Also I link other partition's folders into my /home and some tools show that so my 25GB / is reported as 125GB with the 100GB data partition or parts thereof.

       MB vs MiB
[http://en.wikipedia.org/wiki/Binary_prefix](http://en.wikipedia.org/wiki/Binary_prefix)
[http://www.osforge.com/news/001337.html](http://www.osforge.com/news/001337.html)
Then when you format it, the ext4 is journalized so it reserves space for the journal. This improves performance and allows error correction for the cost of a small amount of space. Also reserves space.
[http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/](http://blog.flexion.org/index.php/2010/01/07/recovering-reserved-space-ext4/)
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)


 1 Gigabyte (GB) = 1,000,000,000 bytes.
1 Gibibyte (GiB) = 1024x1024x1024 = 1,073,741,824 bytes
160 GB (gigabytes) = 149.01 GiB (gibibytes)
sudo parted -s /dev/sda unit GB print
sudo parted -s /dev/sda unit GiB print

Back when drives were small they set 5% as reserved space to help prevent you from crashing system by filling it too full. But with new multi-TB drives that 5% may be too much or not required for data partitions.a But you still are responsilbe for managing your space and once a drive gets 80% full it is time to houseclean or get larger drive.

 Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3

---

### Post by meta_qoph on 2013-11-12
Thank you for the reply, when I set reserved blocks to 0 I found:

```

~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       825G  129M  825G   1% /home

```

It appears that reserved blocks appeared under neither "available" or "used", but do count towards "size", which accounts for the inconsistency I found. gparted continues to report the same numbers as before, and I infer that the 13.39 GiB reported as used by gparted are consumed (mostly) by the file system itself, and that df and du are not including file system overhead ("size" according to df is size of partition after removing file system overhead, but "size" according to gparted is the actual partition's size, irrespective of the file system on it).

---

### Post by brandonmiller21 on 2013-11-12
I'm seeing the same thing after a recent reboot of my system, but when trying to run tune2fs I get an error:

```
mrblue@Windoge:~$ df -hFilesystem                       Size  Used Avail Use% Mounted on
/dev/sda1                         19G  2.1G   16G  12% /
udev                             1.3G  4.0K  1.3G   1% /dev
tmpfs                            505M  376K  505M   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             1.3G  4.0K  1.3G   1% /run/shm
/dev/sda2                        181M   86M   86M  51% /boot
/dev/sda5                        184G  101M  174G   1% /home
/home/mrblue/.Private            184G  101M  174G   1% /home/mrblue
[I]/dev/mapper/owncloud-owncloudlv  886G  338M  886G   1% /mnt/owncloud

[/I]
mrblue@Windoge:~$ sudo tune2fs -l /mnt/owncloud/
tune2fs 1.42 (29-Nov-2011)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /mnt/owncloud/
Couldn't find valid filesystem superblock.


mrblue@Windoge:~$ sudo du -sh /mnt/owncloud/
138M    /mnt/owncloud/
```

---

