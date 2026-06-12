---
title: "Cannot mount Audio CD in Ubuntu Feisty Fawn"
date: 2007-04-29
forum: General Help
---

### Post by tuanduc on 2007-04-29
When I insert a CDROM into my cd drive, it seems to be read  but nothing happens then. Feisty Fawn doesn't mount the CD automaticaly and I have to run sudo mount /dev/cdrom from terminal. The biggest problem is everytime I tried to mount an audio cd, i got the error messages (DataCD can be mount, but manually):
```
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
When I used Edgy, everythings was okey and I can easily play my audio cd. What can I do?

---

### Post by tuanduc on 2007-04-29
I just want to know as if anybody gets the same problem!

---

### Post by capaci on 2007-05-04
i'm having the same problem. can't mount audio cds. anyone have any idea why?

---

### Post by mdurham on 2007-05-04
Quite a few people are having trouble with CD/DVD's, you are not alone.
I hope they fix it soon!

---

### Post by zvacet on 2007-05-05
**system>setting>removable drives&media**

Do you have all boxes cheked?

---

### Post by noneofthem on 2007-05-05
Same problem here. Hope this will be solved soon. Kind of a pain in the neck... This is something very elementary and should not brake on a final version.

---

### Post by sdide on 2007-05-05
you cannot mount an audio CD, there is no filesystem on it. 
Try mounting a normal data CD using 

~$ mount -t iso9660 /dev/<cddev> <mountdir>

If you just want to play an audiocd, you can run gnome-volume-manager and plug it in, 
og just open /dev/<cddev> in vlc or similar problem. 

recap : you are not supposed to be able to mount an audio CD.

---

### Post by mdurham on 2007-05-05
> **sdide said:**
> you cannot mount an audio CD, there is no filesystem on it. 
Try mounting a normal data CD using 

~$ mount -t iso9660 /dev/<cddev> <mountdir>

If you just want to play an audiocd, you can run gnome-volume-manager and plug it in, 
og just open /dev/<cddev> in vlc or similar problem. 

recap : you are not supposed to be able to mount an audio CD.

The problem is not only with audio CD's it's with data CD's and DVD's. I can see the files but can't read them, I/O errors.
I have no problem on Edgy, Dapper or Windows of course.There is a bug report on this and it's marked 'medium' urgency. Figure that one out!
Bug #94119

---

### Post by sdide on 2007-05-05
> **mdurham said:**
> The problem is not only with audio CD's it's with data CD's and DVD's. I can see the files but can't read them, I/O errors.
I have no problem on Edgy, Dapper or Windows of course.There is a bug report on this and it's marked 'medium' urgency. Figure that one out!
Bug #94119

I don't know about that - sorry. 
I have no problem mounting udf nor iso9660 from my optical drive.
But ... if some people try to mount Audio CD's, and  they claim they can't - its not neccesarily because there is something wrong, merely because you aren't supposed to mount Audio CDs.

If there is an issue with Feisty and mounting, its probably because they renamed about every device. 
so 
/dev/hda became /dev/sda, /dev/hdc became /dev/scd0, etc etc.

---

