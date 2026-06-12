---
title: "Nautilus reports wrong NTFS volume (partition) size"
date: 2013-02-10
forum: General Help
---

### Post by cipx2 on 2013-02-10
After I resized my laptop's ntfs partition (using W7 own tools) to make more room for ubuntu, Nautilus reports a wrong ntfs partition size.
Before the resize, the ntfs was 450 GB and was correctly reported by Nautilus.
Now the new size is 400GB and Nautilus says 430 GB

GParted, System Monitor, MountManager, df, fdisk and sfdisk all say 400GB.
Nautilus,  Disk Space Analyzer and Disks all say 430 GB.

The mount options for this ntfs partition are:
defaults,nosuid,nodev,locale=en_US.UTF-8

I unmounted ntfs, removed the entry from fstab, rebooted, Nautilus says the same 430 GB  on the 'new' partition. Reverted back, same thing.

Any clues please?
Thanks

---

### Post by thermion on 2013-02-10
Do you still get this error message after manually mounting the NFTS partition?

---

### Post by Morbius1 on 2013-02-10
Depends on your definition of GB ( I guess more precisely the difference between a Gigabyte and a Gibibyte ) 

Is it 1,000,000,000 bytes? ( Gigabyte )

Or is it 2^30  ( 1,073,741,824 ) bytes? ( Gibibyte )

400 * 1.073741824 = 429.4967296 ( ~ 430 )

---

### Post by cipx2 on 2013-02-10
thermion, yes, no diff.

Morbius1, whatever my definition is, I'm sure it didn't change together with the ntfs partition resize.  As I said, before the shrink the reported size was right and now it is wrong.
Since you asked, my understanding of 1 GB is 1024 x 1MB = 1024 x 1024 x ...
A Gibibyte is symbolized GIB, which is a different thing.

---

### Post by Morbius1 on 2013-02-10
>  Since you asked, my understanding of 1 GB is 1024 x 1MB = 1024 x 1024 x ...Nope. That's from before the year 2000. Back in those days 1024 was the number of bytes in a kilobyte. 1024 is now the number of bytes in a kibibyte. So:
1GB = 1000 x 1000 x 1000  = 1000000000 bytes
1GiB = 1024 x 1024 x 1024 = 1073741824 bytes
> whatever my definition is, I'm sure it didn't change together with the  ntfs partition resize.  As I said, before the shrink the reported size  was right and now it is wrong.Now there you got me. It seems to me you have a choice. It was either wrong before and now its right or it was right before and now it's wrong.

Run the following command to list your partitions and force the output in GiB:
```
sudo parted -s /dev/sda unit GiB print
```Then run the command to force the output in GB:
```
sudo parted -s /dev/sda unit GB print
```
I'm guessing one says 400 the other 430.

---

### Post by cipx2 on 2013-02-10
Your guess is obviously right.

To make things more confusing for me, I just run the live ubuntu 12.10 and Nautilus says the same 430 GB (not 400 - the value in GiB).

One explanation could be that the old ntfs partition was 450 GB and the new one is 400 GiB. The point is I was the one sizing the partition both times (couple of weeks apart) and I used the same technique to multiply the desired value of gigs with 1024.

Anyway, it seems there's nothing wrong with my current ubuntu install so I'll mark this thread as SOLVED (while I'm still sane).

Thanks for the help.

---

