---
title: "How to batch set file's mtime to equal their crtime?"
date: 2021-11-21
forum: General Help
---

### Post by User-007 on 2021-11-21
Hi,

I have a bunch of jpg's. Unluckily, nor EXIF data neither file modifying time shows me the correct time of taking some images (this is due to my wife's way to take the photos and think the date settings after that or never :) ). 

Figured out that there is a "crtime" information on EXT4 systems. Obviously (which is very interesting), the "crtime" shows the correct time.

So. I have two alternative approaches.

How to 

(1) rename .jpg files after their crtime?

OR (If (1) is impossible)

(2) batch set .jpg last modifying time to their crtime (I can batch rename files after their last modify time)?

---

### Post by Impavidus on 2021-11-21
I'm puzzled.

When the camera creates a picture, it makes a jpeg file and (normally) stores the creation time according to the camera's clock in the exif data. Then it stores the jpeg file on its sd card and adds the creation time to the metadata in the filesystem.

When you copy the file from the camera to the computer, the copy tool may: (A) simply create a new file, with the creation time in the filesystem metadata set to the time when the file was copied; or (B) with more advanced settings, create a new file, but set the creation time to the same creation time set on the filesystem on the camera's sd card (it could use the modification time instead); or (C) for specialised photo managing tools, it may set the creation time to the time extracted from the exif data. But when the camera doesn't store the correct time in either the filesystem metadata or the exif data, there's no way for a file manager to know the correct time.

So you have to find out where nemo gets the right creation time, because it must be stored somewhere, either in filesystem metadata or embedded in the image file. You can extract this information using command line tools (stat for filesystem metadata, exif for exif data; you may have to install exif first). Then you can use it in a script to rename the file.

I really prefer to keep image creation times and descriptions embedded in the file. That way you won't loose this information when moving the file around.

---

### Post by User-007 on 2021-11-21
Thank you for your reply. I appreciate it.

I am sorry I edited the original post after your reply with some additional information.

So, EXT4 filesystem includes "crtime" which appears as "Creation time" for nemo.

I investigated a little bit more. The crtime seems to be same in multiple files. So this time has to be the time when saved to the disk. It is much better than the EXIF data of those files. And yes - I have teached my wife to set the date and time before starting to take any shots.

So, my simple question is:

How to batch set the modify time values to crtime values?

---

### Post by Impavidus on 2021-11-21
```
stat --format=%w filename
```will show the file creation time. You can use some bash string manipulation if you wish and use that to rename the file directly. You can set it as the modification time by using touch:```
touch -m --date=STRING filename
```

---

### Post by User-007 on 2021-11-22
Thank you.

AFAIK ”crtime” is not supported by ”stat” command. Your first command does nothing. Haven’t tried second command yet.

---

### Post by Impavidus on 2021-11-22
If I get this correctly, the stat() system call only supports time of last access, last modification and last status change, and the statx() system call is required to get the time of creation. The stat command line tool uses this statx() system call and shows all four timestamps – at least, it does so on my 21.04 system.

Have you checked the manual pages?```
man stat
man -s2 stat
man statx
```

---

### Post by User-007 on 2021-11-22
Sounds tricky.

But, I found this page [http://moiseevigor.github.io/software/2015/01/30/get-file-creation-time-on-linux-with-ext4/](http://moiseevigor.github.io/software/2015/01/30/get-file-creation-time-on-linux-with-ext4/) .

With a simple script, crtime can be extracted easily. Combined this with a patch file renaming script, I managed to rename the names. 

The modification times still differ from file creation times, but actually this is not a big issue.

---

