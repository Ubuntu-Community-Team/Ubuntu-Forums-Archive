---
title: "Restore HD"
date: 2008-03-28
forum: General Help
---

### Post by dareofficer on 2008-03-28
Hello, I have Ubuntu 7.10 and it works great, works so great I got another PC just to run it.  My question is I have it my first PC as a dual boot.  Is there a way to remove the dual boot and restore it to Windows only?  I have Ubuntu on my other PC alone, and hope I don't have to restore my PC from scratch?

---

### Post by Rocket2DMn on 2008-03-28
Sure, you can use the GParted LiveCD to delete the Ubuntu partitions (root, swap, and /home if you have it).  Then you can resize the windows ntfs partition to use the newly freed disk space.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
After you get rid of Ubuntu, you will need to restore the windows MBR to get rid of GRUB.  This can be done by booting from your windows disc, entering the recovery console, then running
```
fixmbr
```

---

