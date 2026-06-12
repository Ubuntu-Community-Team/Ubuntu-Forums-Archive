---
title: "can someone explain Free versus Available disc space please"
date: 2007-06-06
forum: General Help
---

### Post by mdurham on 2007-06-06
Please see attached pic and then can someone explain why on hda6 for instance
Free == 15.4 Gb  Available == 14.4 Gb what does it mean?
Just to confuse things, Nautilus reports hda6 Free space == 14.4 Gb

The question is why doesn't Free equal Available? 
What does 'Free' mean?
What does 'Available' mean?
Why on all of the ext3 file systems do Free and Available differ?
Why is it so complicated?????

Cheers, Mike

---

### Post by taurus on 2007-06-06
If you are using ext3 filesystem, 5% of the disk space is reserved for root in case you fill up disk space and you can't log in anymore.  That's why 15.4GB is free but you can only use 14.4GB of it.  The other 1GB is reserved.

---

### Post by mdurham on 2007-06-06
> **taurus said:**
> If you are using ext3 filesystem, 5% of the disk space is reserved for root in case you fill up disk space and you can't log in anymore.  That's why 15.4GB is free but you can only use 14.4GB of it.  The other 1GB is reserved.

Thanks taurus, I would never have thought of that. 
Cheers, Mike

---

### Post by stchman on 2007-06-06
> **taurus said:**
> If you are using ext3 filesystem, 5% of the disk space is reserved for root in case you fill up disk space and you can't log in anymore.  That's why 15.4GB is free but you can only use 14.4GB of it.  The other 1GB is reserved.

Is there a way to limit that?  I mean of you have a 200GB hdd on a partition why do you need 10GB reserved for root?

I did also notice that as well.  I partitioned my hdd and the other partition had that as well.  So no matter what, no matter how many partitions, you will give 5% of each partition to root?

---

### Post by mdurham on 2007-06-08
I've just had a look at my external backup discs.

Total.38.8 GB
Free 2.6 GB 
Available 647.8 MB
Used 36.2 GB
Why has a 2 GB chunk been made unavailable? This is not a system disc only backup.

On my other 28.2 GB external USB backup drive I loose 1.5 GB
This can't be due to space reserved for root can it?
What can I do about it?

Cheers, Mike

---

### Post by montgoss on 2007-06-08
I had the same question.  I deleted files but  I still had 13.9 GB free and only 2.2 GB available.  It was as if files I deleted weren't actually being removed.  They weren't in the trash.  But they were in a .Trash folder.  Look for those on the root of a partition.  Apparently, if you delete something from a KDE app (k9copy in my case), it might just move it to the KDE trash.  Which you don't see if you're using a default Ubuntu install with Gnome.

As to how to adjust the amount of space reserved for root, use the following command:
```
sudo tune2fs -m 1 /dev/sda1
```
"1" is the percentage reserved.  I've not tried it with 0, but maybe you want to do that on your external drive.

---

### Post by mdurham on 2007-06-08
> **montgoss said:**
> I had the same question.  I deleted files but  I still had 13.9 GB free and only 2.2 GB available.  It was as if files I deleted weren't actually being removed.  They weren't in the trash.  But they were in a .Trash folder.  Look for those on the root of a partition.  Apparently, if you delete something from a KDE app (k9copy in my case), it might just move it to the KDE trash.  Which you don't see if you're using a default Ubuntu install with Gnome.

As to how to adjust the amount of space reserved for root, use the following command:
```
sudo tune2fs -m 1 /dev/sda1
```
"1" is the percentage reserved.  I've not tried it with 0, but maybe you want to do that on your external drive.

Thanks for the info montgoss, I'll try it tomorrow I'm a bit tired now.
Cheers, Mike

---

