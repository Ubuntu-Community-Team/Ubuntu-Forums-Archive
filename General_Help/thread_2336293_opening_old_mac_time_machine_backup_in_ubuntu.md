---
title: "opening old mac time machine backup in ubuntu"
date: 2016-09-06
forum: General Help
---

### Post by Bhakti108 on 2016-09-06
Hoping I can get some help with this. I have an external drive with my old backup on it from mac days. I need to access some files. I followed a hint on Macworld here [http://hints.macworld.com/article.php?story=20080623213342356](http://hints.macworld.com/article.php?story=20080623213342356) but when I get to the part regarding changing into the hidden directory .HFS+ Private Directory Data? I get "Dir or file does not exist. I am root when I try this. 

I have opened Nautilus as root, and can see the directory and all its sub directories, I can even find the one I want and open it, but cannot copy or access the files because permission is denied. However in terminal I cant access the directory at all. 

Does anyone know what I need to do to get into the data directory and then be able to copy files across onto my hard drive so I can view and use these files with full read write permissions

Cheers

---

### Post by &amp;KyT$0P# on 2016-09-06
This sounds like something I had tried to do.  The problem is that Ubuntu sees the HFS+ hard links as 0-byte files, this including hard links were actually to directories.
I came to the conclusion that Mac OS X is required.

I don't remember how I ended up using Mac OS X to transfer my data though. :?

---

