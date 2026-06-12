---
title: "File System Full"
date: 2008-02-26
forum: General Help
---

### Post by LAF4SENS on 2008-02-26
Hi,

I'm new to Linux world and Ubuntu. I booted my pc and UBUNTU told me that my File System was full.

In deed, I went to the file browser and clicked on FILE SYSTEM and it has 0 bytes left.

What can I delete with out doing any damage to UBUNTU, I also have another partition with 27 MG of freespace. Can I tell UBUNTU to use that partition for the File System ??

Please Help,

Thanks,
Marc.

---

### Post by Sam Lars on 2008-02-26
Where is all this space being eaten?
You can delete your trash (~/.Trash)
You could also try a
```
sudo apt-get clean
```

---

### Post by seventhc on 2008-02-26
How much total space did you originally give ubuntu when you installed it?

---

### Post by Front187 on 2008-02-26
I had a simliar problem at one point.  It turns out that something had created a file (it was named install.something, i forget what exactly the extention was.  Anyway, it was the size of the remainder of my disk space.  I just deleted it, and everything was fine after that.

I forget where it was.

Check 
/
/etc
and your home folder

I believe it was in one of those.

---

