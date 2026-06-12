---
title: "Too much cached ram"
date: 2013-07-02
forum: General Help
---

### Post by Pantzintown on 2013-07-02
Hello 

 i am running ubuntu 13.04 and everything is working fine but when i start to transfer files it comes to a complete near the end. i read up and figured it was the cached ram. when i looked it came
             total       used       free     shared    buffers     cached
Mem:          7806       7255        550          0         51       6340
-/+ buffers/cache:        863       6943
Swap:         8008          0       8008

can anyone help me get rid of all of the cached memory or help me understand why its so much ive only beeen using this version for a week now and only downloaded chromium and the netflix web app.

thanks

---

### Post by 3rdalbum on 2013-07-03
Cache is not a problem. It is only there for file copying and to make certain things faster. If tgr computer needs more RAM than is available, it will remove some cache automatically. In short, cache is not your problem. Ever.

It sounds like you are trying to copy large files to a disk with the fat32 filesystem. Fat32 can not store files over 4 gigabytes. Format the destination disk to NTFS or Ext4 and try again.

If this isn't the problem, please describe the problem again in more detail and tell us exactly what error message you get.

---

### Post by Cheesemill on 2013-07-03
Cached RAM is a good thing. It just means that programs will start quicker.
For an explanation check out this page...

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by slickymaster on 2013-07-03
It's normal. Linux aggressively allocates RAM to disk cache and there is no good reason to freeing it up again until it is needed by some other process. As other processes need RAM, the balance between disk cache and process allocation will be managed. In short, don't worry.

---

### Post by Pantzintown on 2013-07-03
thans i tried changing the format and it worked so much better

---

