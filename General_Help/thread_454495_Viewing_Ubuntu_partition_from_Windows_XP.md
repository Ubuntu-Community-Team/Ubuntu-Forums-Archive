---
title: "Viewing Ubuntu partition from Windows XP"
date: 2007-05-25
forum: General Help
---

### Post by bootsbradford on 2007-05-25
I have set up a dual boot system whereby my PC boots into ubuntu by default but gives me the option of booting into windows if desired.

If I boot into ubuntu, I can access the windows partition easily. However, I am suffering from the Ubuntu freeze problem at the moment, so have had to switch back to windows by default...

What I am trying to work out is how I do the reverse: **How can I get hold of files I have saved in my Ubuntu partition and use them from my windows partition?**

(The only solution I can do at the moment is to boot into ubuntu and copy them across, but I am sure there must be a way to do it from windows)

---

### Post by balak on 2007-05-25
The answer depends on your partition structure. If you have a FAT32 or NTFS partition that you were using as /data or something on ubuntu, you can see that in windows.

If you had only EXT3 partition, AFAIK you cannot access it from windows.

---

### Post by merlinus on 2007-05-25
Install ext2ifs from their website.  It works fine with ext3 also. For me, anyway....

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by bootsbradford on 2007-05-26
> **merlinus said:**
> Install ext2ifs from their website.  It works fine with ext3 also. For me, anyway....

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

Fantastic tip, set up within a minute and did just what I wanted. Thanks very much!!

---

