---
title: "casper-rw available space"
date: 2013-12-10
forum: General Help
---

### Post by tendouser on 2013-12-10
is there a way to check how much space is left free for storage in casper-rw?

---

### Post by ajgreeny on 2013-12-10
You can mount the casper-rw file from the CD/DVD, though I am ot sure if you can do this when running the live system itself.
Worth trying I think: just make a directory to mount it in with
**sudo mkdir /media/casper**

and then mount it
**sudo mount -o loop casper-rw /media/casper/ 			 		**

You should then be able to see the size of the files in the casper-rw and relate that to the overall casper-rw size.

---

