---
title: "HD with unusable sectors"
date: 2006-08-07
forum: General Help
---

### Post by remusus on 2006-08-07
At least one of the sectors on my hard drive is unusable, I've been getting the click of death lately on a large downloaded files.  I'm using reiserfs partitions.  Right now I've got it contained within a 400MB file, but I can't get reiserfschk to find any problems.  How can I get the unusable sectors marked as such?  I don't want to end up with some critical data written over the sectors, so for now I'm leaving the big file there, but I want to get rid of this file sometime...

---

### Post by fourchannel on 2006-08-07
if you can find out the block size you used for your filesystem then these commands could work for you

1.) is badblocks, it needs the blocksize of the filesystem in questions to accurately perform a non-destructive read/write test. It is **imperative** that you get the correct block size or this might screw your partition seven ways till sunday.
2.) is reiserfstune, which will allow you to add a badblocks list

the way this works, badblocks runs and saves the list to a file. You then tell reiserfstune to use that file to add the badblocks list to the filesystem.

I'm assuming that /dev/hda1 is your partition in question, you need to change the code accordingly.


```
badblocks -b blocksize -n -o /location/of/badblocks/list /dev/hda1
reiserfstune -B /location/of/badblocks/list /dev/hda1
``` 
You will need to umount the partition before scanning it, most likely you will need to download a live cd and use that. 40gb harddrive is a decent size and it will probably take hours to do a thourough scan, so you need to either browse the internet or whatever during that time.

remember, modifying a filesystem is dangerous and great caution must be employed when doing so. You need the blocksize of the filesystem or the badblocks list will report wrong sectors and you will lose data or corrupt of FS. you can type the following  to look up more options and help. ```
man badblocks
man reiserfstune
``` Let me know if you come across any problems.

---

### Post by remusus on 2006-08-07
Very informative, thanks.  I determined the blocksize using 'debugreiserfs', and after that it's quite easy.  Thanks.

---

