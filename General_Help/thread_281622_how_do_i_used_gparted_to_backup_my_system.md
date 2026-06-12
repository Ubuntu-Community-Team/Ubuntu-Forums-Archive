---
title: "how do i used gparted to backup my system?"
date: 2006-10-21
forum: General Help
---

### Post by maddbaron on 2006-10-21
I'd like to back up my system.

Mainly the root with all the installed programs and custom stuff I've done so I can either do a fresh upgrade to edgy or a fresh reinstall of kubuntu since I want to redo my partitions and remove xp and the ways I've read how to repartitions make my head hurt.

I downloaded k9copy but i dont understand it even though it says its for system back up.

I read I can use gparted, when I open it the copy option on paritions is not working.

Can anyone assist me please?

---

### Post by podunk on 2006-10-21
Can't answer the question about gparted - but this works really good. :-)
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/media --exclude=/sys /
```

from post 210 on this page:
[http://www.ubuntuforums.org/showthread.php?t=35087&page=21](http://www.ubuntuforums.org/showthread.php?t=35087&page=21)

Before you run it - unmount your windows drives and make sure you don't have any DVD's in drives! :mrgreen: 

The first time I did it I left all my windows drives mounted and had a movie in both my DVD drives - I ran out of free space before I ran out of backup.

Once I fixed that it backed my system up in less than 30 minutes, 10+gigs was compressed down to 3 and you can use Archive Manager to extract individual files or directories

---

