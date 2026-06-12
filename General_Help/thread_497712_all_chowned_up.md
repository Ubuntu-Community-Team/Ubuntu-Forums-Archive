---
title: "all chowned up"
date: 2007-07-10
forum: General Help
---

### Post by jackzoe on 2007-07-10
I have been using ubuntu for a couple of weeks, got it networking with my windows computers  and to work with my canon printer. I used chown to change owner of smb.conf file so I could modify it and it worked ok ! I have a 250gb second drive which it sowes as "New Volume" I have tried everything but cannot change the owner from root to myself. this is one of the things I get.
pop@linux:~$ sudo -i
root@linux:~# chown pop /media/New Volume
chown: cannot access `/media/New': No such file or directory
chown: cannot access `Volume': No such file or directory
root@linux:~# 
I thought root could do anything! I pasted the path off the file browser

---

### Post by tgoose on 2007-07-10
Try ```
chown pop "/media/New Volume"
```

The terminal assumes that a space means the end of something, and it looks like chown is trying to act on two different files because of that. The quotation marks tell it that it's actually one path.

---

### Post by jackzoe on 2007-07-10
tea ready try it in 10 min

---

### Post by pistcivet on 2007-07-10
I think the quotes will work, but here is another way to do it:
```
chown pop /media/New\ Volume
```
The "backslash space" tells bash that the space is part of the filename.
Can also be used for other special characters.

---

### Post by jackzoe on 2007-07-10
no luck tried both ways this was the reply on the second
pop@linux:~$ sudo chown pop /media/New\Volume
Password:
chown: cannot access `/media/NewVolume': No such file or directory
pop@linux:~$ sudo -i
root@linux:~# chown pop /media/New\Volume
chown: cannot access `/media/NewVolume': No such file or directory
root@linux:~# 

as you can seeIchanged it to root with no luck why does it say no file or d when I can open it?

---

### Post by pistcivet on 2007-07-10
You left out the space.
this: pop /media/New\ Volume
not this: pop /media/New\Volume

---

### Post by jackzoe on 2007-07-10
yes your right but I had already noticed this before you replied and tried again with no luck . But I noticed under the file system the media file had no lock on it when I checked it the owner had changed to "pop" so I tried it on the home folder and that changed to "pop" .oldies like me must be a bit thick must be doing something wrong!

---

