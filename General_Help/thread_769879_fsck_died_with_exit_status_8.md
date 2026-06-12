---
title: "fsck died with exit status 8"
date: 2008-04-26
forum: General Help
---

### Post by Lord Xeb on 2008-04-26
I was trying to resize my partition with Gparted (on the Ubuntu LiveCD), but I clicked cancel... I think that was a bad idea. When I went to boot, it will go through then go to a black screen with a flash cursor. When I go into recovery, it will get to the part that it checks the file system, then it will say

Code:

checking Files Systems fsck 1.4.2
fsck.ext3 unable to resolve 'UUID=8ac63799-2a29-4668-90cd-1cf6fc3a6a8e'
fsck died with exit status 8


I have looked all over for help and so far nothing has D:

Please help!

---

### Post by scragar on 2008-04-26
if you've got a live CD this would be a good time to use it, if not things get harder.

you will need to edit your fstab file, and change the UUIDs to the path above them, from the liveCD run```
gksudo gedit /etc/fstab
``` from the shell you'd have to run ```
vi /etc/fstab
```and use i to enter typing mode, adjust the line, then use escape to exit to normal mode to save etc. I'm afraid I'm not all that good with vi...

---

### Post by Lord Xeb on 2008-04-28
to late, I already formated

---

