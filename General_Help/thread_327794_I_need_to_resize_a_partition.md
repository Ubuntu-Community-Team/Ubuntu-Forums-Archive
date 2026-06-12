---
title: "I need to resize a partition"
date: 2006-12-29
forum: General Help
---

### Post by Vord on 2006-12-29
So, when I installed ubuntu I figured I would leave a nice chunk of my hard drive to windows, thinking I'd be doing a great deal of gaming that required it, when really all I need it for is raids in WoW, and occasionally BF2142. I left 40gb to my windows partition, and two games does NOT require that much. I was wondering how I would go about resizing both my ext3 partition and my NTFS windows partition, without screwing anything up.

---

### Post by ndube on 2006-12-29
> **Vord said:**
> So, when I installed ubuntu I figured I would leave a nice chunk of my hard drive to windows, thinking I'd be doing a great deal of gaming that required it, when really all I need it for is raids in WoW, and occasionally BF2142. I left 40gb to my windows partition, and two games does NOT require that much. I was wondering how I would go about resizing both my ext3 partition and my NTFS windows partition, without screwing anything up.

install gparted (sudo apt-get install gparted). this will allow you to graphically resize both partitions. If you prefer to do it outside linux, google gparted and download the live cd. This will allow you to resize the partitions from a cd.

---

### Post by taurus on 2006-12-29
Technically, you can use gparted from the LiveCD to make your Windows smaller and merge that extra space into Linux.  And of course, _ALWAYS_ backup your data before you start resizing your harddrive just in case...

---

### Post by Vord on 2006-12-29
Ahh, thanks a lot, I'll let you know how it worked out

---

### Post by shane2peru on 2006-12-29
Whenever you play with the partitions you had better back up, as there is a risk involved in resizing.  As for you Windows, make sure you defrag your harddrive.  Clean off any unwanted things.  Afterward from inside Ubuntu, you can resize that partition using Gparted.  You may have to install it.  Go to **System - Administration - Synaptic Package Manager**  do a search for Gparted and get that installed.  Next go to **System - Administration - GNOME Partition Editor**  You will see your NTFS partition and you can resize that.  As far as your ext3 probably not, it may be better to just format that space you take from Windows and make a separate partition out of it, and use it for storage. 

Shane

---

### Post by shane2peru on 2006-12-29
I guess NDUBE wins the typing award for speed!

Shane

---

