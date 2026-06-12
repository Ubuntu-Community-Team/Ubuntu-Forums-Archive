---
title: "Best file system for a backup solution?"
date: 2007-10-15
forum: General Help
---

### Post by stuporglue on 2007-10-15
I finally got around to buying to 500 GB USB hard drives to use as a backup solution. One will remain at home for the week, the other off-site. I have little enough new data that rotating them weekly or bi-weekly will keep me happily recoverable in case of disaster. 

The question I have is: What file system should I use for the disks? 

Factors: 
[LIST]
[*]]My most critical data is photos from my wife's photo business, each between 5 and 10 Mb. The photos also make up the most of the storage. 
[*]I will more than likely have some files larger than 4GB, which means no FAT32. 
[*] The data won't be changing much or often. Every week or so I will be adding 2-3 Gigs of photos, but the old photos rarely change.
[/LIST

I've heard that ReiserFS makes better use of the disk space, especially with small files, but how small is small? Are the 5-10Mb photos considered small? 

In the case of drive failure or a file system crash what is the most recoverable option? ReiserFS, Ext2, Ext3, other? 

Thanks, 
Michael

---

### Post by atlfalcons866 on 2007-10-19
ext3. If reiserfs goes down it stays down

---

### Post by stuporglue on 2007-10-20
Thanks atlfalcons86, 

I ended up going with ext3, and so far so good. Feels good to finally have offsite backup. :-)

---

