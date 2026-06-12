---
title: "What's the best file system for 750 GB USB Drive?"
date: 2008-05-19
forum: General Help
---

### Post by tankerkevo on 2008-05-19
I recently purchased a 750 GB Seagate FreeAgent USB drive. It will mainly be used as a file and media server. The catch here is that my client (laptop) runs Hardy, but the actual drive will be attached to a Fedora 8 Server box. Not sure if that really matters...but worth mentioning.

I already have a 500 GB FreeAgent on the system formatted to HFS+ (Apple File System). I need this 500 GB drive to be HFS, but I've found that either the HFS file system is crap, or probably more likely, Linux is having a difficult time properly managing it as it constantly needs to get fixed.

So, that said, what Linux friendly file system should I use? Ext2, Ext3, Ext4, or something completely separate?

---

### Post by latna on 2008-05-19
Well, I would chose ext3 over ext2 or ext4 at this point. ext2 isn't journaled, and AFAIK ext4 is still in beta. But whatever you chose will prolly be fine.

Personally I have a 500GB drive I use for data and I formatted it with xfs as one big partition. I actually tried both ext3 and xfs and ext3 used a significant amount more space just for the filesystem. I want to say it was several GB but I could be way wrong in remembering that.

Others will have their own preference but that's just my experience. My main OS partition is ext3 for what that's worth.

HTH

---

### Post by tankerkevo on 2008-05-19
Did some research on XFS. Seems to be good for large media files (movies). Also says to be careful that you make sure you shutdown properly...its a server so shutdowns are rare, once every three months maybe. 

Drive is formatted to XFS and is kicking but.

Thanks for the advice!

---

