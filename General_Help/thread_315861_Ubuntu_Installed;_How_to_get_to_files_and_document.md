---
title: "Ubuntu Installed; How to get to files and documents on old Harddrive?"
date: 2006-12-09
forum: General Help
---

### Post by Zetabug on 2006-12-09
I recently installed Ubuntu and was wondering how I could get the files from my harddrive from when I had windows or how to get to my harddrive in general. Thanks for any help.

---

### Post by aysiu on 2006-12-09
Same computer, different drives?

This should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Zetabug on 2006-12-09
This might seem kinda of like a stupid question but where exactly do you open a terminal from?

---

### Post by aysiu on 2006-12-09
A guide is in my sig, but I'll link to it again:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

---

### Post by Zetabug on 2006-12-09
GNU nano 1.3.12             File: /etc/fstab                                  

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

















                                [ Read 2 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell


That is currently what it looks like after I typed: sudo nano /etc/fstab
Not sure what to do next since it doesn't look like what the walkthrough shows it to be.

---

### Post by aysiu on 2006-12-09
Are you running off the live CD?

---

### Post by Zetabug on 2006-12-09
ya Think so. Is that a problem?

---

### Post by aysiu on 2006-12-09
> **Zetabug said:**
> ya Think so. Is that a problem?
Nope. Not a problem. Just no point in editing the /etc/fstab if it's just going to be wiped out the next time you reboot. Can you post the location and filesystem of the drive you're trying to mount?

For example: /dev/hda1, NTFS; or /dev/hdb2, FAT32

---

