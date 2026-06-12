---
title: "NTFS partitions suddenly disappeared"
date: 2007-05-14
forum: General Help
---

### Post by blax on 2007-05-14
I had Ubuntu 7.04 set up so that I could read my NTFS partitions, and all was well. I recently booted into XP for a moment to fix my MP3 player which died on me, and when I booted back into Ubuntu the partitions are no longer available. 

I can no longer see the partitions at all, and I have absolutely no idea what to do! :confused:

//edit: Got it working, thanks you guys!

---

### Post by taurus on 2007-05-14
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by earobinson on 2007-05-14
you could try ```
sudo mount -a
``` (That should remount everything)

---

### Post by blax on 2007-05-14
-snip-

---

### Post by blax on 2007-05-14
-snip-

---

### Post by taurus on 2007-05-14
Looks like you need to boot into Windows and defrag and shutdown your machine first before you can mount it in Ubuntu.

---

### Post by blax on 2007-05-14
Yeah, I got it working. I just booted into XP and shut it down again.

Quite odd.

---

