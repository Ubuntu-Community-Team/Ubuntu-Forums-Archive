---
title: "Firewire Drive"
date: 2007-04-08
forum: General Help
---

### Post by jessej on 2007-04-08
Hello Everyone.

I Installed Ubuntu a few weeks ago and Everything is working GREAT!
I am very impressed.

I am having a problem with my Firewire hard drive though.  This was also a problem back when I had WINDOWs2000.  For some reason the drive is recognized by the system  if I go into the Device Manager but I can't get it open.  I was hoping after installing Ubuntu that it would just work, but alas this problem persists.  

The fire wire Drive is a 30gig Western Digital.  Anybody have any ideas?

Thanks You
JesseJ

---

### Post by strabes on 2007-04-08
Install ntfs-3g so that you can read and write to the ntfs filesystem.

```
sudo apt-get install ntfs-3g
```

---

### Post by jessej on 2007-04-09
Thanks for the reply,

I think that the drive may be formatted for a Mac.  What would I need to install then?

---

