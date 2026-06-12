---
title: "chmod on my server"
date: 2007-09-15
forum: General Help
---

### Post by bone2006 on 2007-09-15
I recently installed an ubuntu server (LAMPS) and I uploaded the forum SMF to var/www/forum
Which forum I created.

Well I opened up the install.php file and it tells me which folders/files I need to change premissions on and the first folder is attachments, which I tried typing in 
chmod 777 attachments and then I went back to the install.php and click to retest it and it still shows up as not changing it's properties.

So I typed in:

touch attachments
chmod 777 attachments
ls -l attachments

total 4
-rw-r--r-- 1 nobody 99 327 2007-06-24 21:16 index.php

I noticed that when I went into the directory above it and ran

ls -ls forum
I see the two folders I tried turned green and shows root next to them

Any idea how I can change these permissions to get the forum up and running?

---

### Post by bodhi.zazen on 2007-09-15
Ubuntu uses sudo and it sounds as if those files are owned by root.

```
sudo chmod 777 /path/to/file
```

---

### Post by bone2006 on 2007-09-15
that's not the problem, I should have clarified, sudo is already being used on all the commands.  I should have been more specific...sorry about that

---

### Post by bone2006 on 2007-09-15
I'm wondering if it's because it's in a directory that already doesn't have write permissions and it's a level deeper.

most tutorials say to do sudo chmod 777 /var/www

but I want the forum to be located in /var/www/forum

So I just did sudo chmod 777 /var/www/forum/attachments

---

