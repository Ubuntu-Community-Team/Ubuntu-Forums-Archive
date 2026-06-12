---
title: "Copy etc folder to pendrive"
date: 2006-11-27
forum: General Help
---

### Post by ruialexbarbosa on 2006-11-27
I will probably need to reinstall Ubuntu, but I was told I can save my "etc" folder and then copy it back after the reinstall to reconfigure my system.

I tried through the livecd, but it won't let me copy most of the files, looks like a permissions problem. I tried as root and the same thing happens...](*,) help?

---

### Post by cilynx on 2006-11-27
Why are you looking to reinstall?  Generally when reinstalling, the advice is to keep your home directory as opposed to /etc.  /etc has your system settings and will most likely bring your problems with it to your new installation if you copy it over.  So let's start there.  What's going on to force the reinstall?

---

### Post by ruialexbarbosa on 2006-11-27
Hi,

thanks a lot for your answer. I'm trying to keep the settings on my ubuntu edgy because it won't restart.

I don't need my files because they are on another partition (Fat32) but would like to keep my printer, scanner, and other settings, and was told they are in etc.

I posted the problem in another post, here's a copy of what I wrote:


Hi,

I'm on edgy and now I can't boot.

The system is starting and it crashes checking file systems. It says something like this:

* Activating swap... OK
* Checking root file system...
fsck 1.39 (29-May-2006)
/dev/hda7: clean, 124286/2088960 files, 765807/4176892 blocks (check in 2 mounts)

* Checking file systems...
fsck 1.39 (29-May-2006)



And then NOTHING happens. By the way, I believe hda7 is my ext3 partition (or could it be the fat32 drive I use for my files?)

Thanks for any help, it would be much apreciated.

---

### Post by cilynx on 2006-11-27
From your output there, /dev/hda7 is fine.  It's the next one that's having issues.  Do you know what is after hda7 in your mount order?

---

### Post by ruialexbarbosa on 2006-11-27
I think it's my swap file, but it could be the fat32 drive. I setup the partitions this way:
1 NTFS (WIN)
2 FAT32
3 EXT3
4 SWAP

---

### Post by cilynx on 2006-11-27
If fsck is messing with it has to be an ext filesystem.  You don't fsck swap and fsck won't automagically go after any Windows partitions.  hda7 is your /.  Do you have any other partition mounted as ext filesystems?

---

### Post by ruialexbarbosa on 2006-11-27
no...

---

