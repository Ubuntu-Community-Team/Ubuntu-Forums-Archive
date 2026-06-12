---
title: "Recovering &quot;unreadable&quot; AVI files"
date: 2008-05-20
forum: General Help
---

### Post by dehughes on 2008-05-20
Hello all,

I have a hard drive from my old computer, and this hard drive has Ubuntu 7.10 installed on it.  I really need to get some videos off of the hard drive, but only 5 of the 31 are "readable" and the rest show up as "unreadable", with the "unreadable" icon appearing next to the file.  These were AVI files taken by my digital camera, and all worked just fine when the hard drive was installed in my other tower.  However, I've taken that computer apart, and THOUGHT I copied all the files over...only to find that 26 of the 31 videos did not transfer. SO, I'm running that old drive via a SATA hard drive dock, but cannot get the videos to show up as readable and thus copyable.  Most every other file can be transferred, which is frustrating, as these video files are the important ones!  :)

ANY suggestions will be greatly appreciated, as I'm kinda stuck...  Do I need to change the file type, or change permissions, or???  When I try to copy the files over to my new computer I get errors that say "Error opening file: Permission denied".  

THANKS SO MUCH!

---

### Post by tamoneya on 2008-05-20
```
sudo chmod 777 myfile.avi
```

---

### Post by dehughes on 2008-05-20
> **tamoneya said:**
> ```
sudo chmod 777 myfile.avi
```

Right on.  Many thanks.  Now, will this work via a "live" boot CD?  I'm using a Ubuntu disk running off ram via my brother's computer as we don't have another Ubuntu machine handy.  

I assume the 777 enables everyone to own it...

The odd thing is that all 31 videos show as "1000", but then only 26 of them are unreadable.  I assume by changing them to "777" will do the trick?

---

### Post by tamoneya on 2008-05-20
yeah it shouldnt matter that you are using the liveCD.  This is making changes to the filesystem which is part of your harddrives.  777 makes it fully available to everybody.  Typically I would say something more lik 755 or 644 but since this is file recovery and it wont result in any security risks its simplest to just say 777.

---

### Post by dehughes on 2008-05-21
> **tamoneya said:**
> yeah it shouldnt matter that you are using the liveCD.  This is making changes to the filesystem which is part of your harddrives.  777 makes it fully available to everybody.  Typically I would say something more lik 755 or 644 but since this is file recovery and it wont result in any security risks its simplest to just say 777.

Right on.  THANKS SO MUCH!  I assume this is done through the terminal? I've not done this before with Ubuntu and don't want to screw this up.  Perhaps there is a page somewhere that would give me more step by step instructions?  I guess it seems odd to me that 5 out of the 31 files would show up as normal AVI files, and the other 26 would be unreadable and unavailable to me...but then, I don't know too much about Ubuntu.

---

### Post by dehughes on 2008-05-21
Also, the 26 unreadable files do not appear as .avi files either, but instead don't seem to have and particular file type...if that changes anything.

---

### Post by tamoneya on 2008-05-21
permissions dont care what the file extension is so it wont matter if it is "myfile.avi" or "myfile.jpg" or even just "myfile".

---

### Post by dehughes on 2008-05-21
Ah, fair enough. I remember changing the file names from "3199.avi" to "barking dog March 15th", dropping off the AVI tag on the end, but then I did that to all 31 files so I still don't understand why 26 of them would suddenly be unreadable.  Odd....all from just removing the hard disk from the computer case.

Anyway, I'll see what we can do in regards to changing ownership/permission of those files, and see if that gets them readable.

---

