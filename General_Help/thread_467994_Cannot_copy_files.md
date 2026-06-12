---
title: "Cannot copy files ?"
date: 2007-06-08
forum: General Help
---

### Post by roar on 2007-06-08
On a ntfs partition on my old disk I have som mp3 i want to copy to a new disk with ext3. I just did 
cp -r /pathold_disk /path_new 

, and the stuff seems to have been cpoied to the new location. However, when trying to plasy the mp3 in amarok a pop up appears and says that 

Error loading media
No suitable plugin found. This often means the urls protocol is not supported. Network failures are other posible causes

Playing the same file located on the old disk works perfectly. what is going on here ? please help

---

### Post by hillbilly on 2007-06-08
you have to first install the mp3 codec for amarok. I think it prompts you for that.  Atleast I remember it doing for me.

---

### Post by roar on 2007-06-08
Thanks for replying. I can play mp3 with amarok, so the codecs are installed. The problem is that I cannot play the files located at the new disk, the files appears to have been corrupted during the copy process.

---

### Post by roar on 2007-06-08
Ok, seems there is an issue with ntfs system. After installing ntfs-3g driver the copy works ok. This was on dapper btw

---

