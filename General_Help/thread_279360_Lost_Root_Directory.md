---
title: "Lost Root Directory"
date: 2006-10-17
forum: General Help
---

### Post by oscabat on 2006-10-17
I have no idea what happened, but the root directory for my Linux hard drive is no longer visible from the file browser.  All I can see is the filesystem drive.  When I go to the Disks Manager, it shows that the harddrive still has two partitions - the swap and the regular partition.  I'm not that Linux savvy, but do I need to worry about the loss of the icon?

---

### Post by taurus on 2006-10-17
Are you talking about /?  If the icon doesn't appear on your desktop, don't worry about it since you can't write to it or modify anything in it unless you use sudo!  So if you see your / with this command (Applications -> Accessories -> Terminal), then everything is good and by the way, if you are able to use your Ubuntu, then you are alright with your / partition...

```
df -h
```

---

### Post by oscabat on 2006-10-17
That's what I thought.  I just found it weird that the icon would all of a sudden disappear like that.  Thanks.

---

