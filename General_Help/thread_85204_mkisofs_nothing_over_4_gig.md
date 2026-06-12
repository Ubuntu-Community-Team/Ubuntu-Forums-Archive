---
title: "mkisofs nothing over 4 gig"
date: 2005-11-02
forum: General Help
---

### Post by engineuity on 2005-11-02
Hi, 
   I am trying to make backup images of files that i have on my hd, but I cant seem to make an image bigger than 4 gigs. I am using mkisofs, and once it reaches that 4 gig mark, I get an error saying it is out of disk space. df -h returns the destination drive has about 98% left out of 30gigs. Anyone else experience this?

---

### Post by xmastree on 2005-11-02
4GB? It's not a FAT 32 partition is it?

---

### Post by engineuity on 2005-11-02
Actually it is on a fat32 partition...the whole reasoning for me backing all this stuff up is so i can switch over to ext3. I guess this is just furthering that goal.

---

### Post by xmastree on 2005-11-02
> Actually it is on a fat32 partition...
There's your problem. FAT 32 can't store files larger than 4GB

[http://www.google.com.ph/search?q=FAT32+4GB+limitation](http://www.google.com.ph/search?q=FAT32+4GB+limitation)

---

