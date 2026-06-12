---
title: "adding vista partion to grub"
date: 2007-03-31
forum: General Help
---

### Post by cptjaben on 2007-03-31
I just installed edgy on my laptop, I did this by resizing my hdd that had vista and making 2 new partions, 1 for ubuntu, and 1 for a swap. So there's a total or 3 partion now,  1 vista, 1 ubuntu, and 1 swap. I also installed grub, however it did not detect vista. Is there a way that I can add vista to grub so that i can choose to boot vista upon startup? Thanks

---

### Post by kellemes on 2007-03-31
This is assuming Windows is the first partition on first disk
Add this entry to your /boot/grub/grub.conf


title           Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1


If not working try to find out what partition Windows is one and find the grub devicename, so "hd0,0" will have to be changed to hd0,1 o hd0,2 etc.. probably..

---

### Post by Dream. on 2007-03-31
Ok, maybe my first post of use to someone, I have just gone through this process myself and was given this link by one of the staff members here. (worked a treat)

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

