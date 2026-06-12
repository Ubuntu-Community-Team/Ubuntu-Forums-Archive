---
title: "[SOLVED] Change var from / mount to different hard drive"
date: 2007-03-11
forum: General Help
---

### Post by prince_niceguy on 2007-03-11
I am having var folder in my root (/) partition. I want to move it to another hard drive so that i can free up some space on root partition.

any suggestion how to do or achieve the same.

thanks in advance

---

### Post by prince_niceguy on 2007-03-11
bump.. sorry need urgently.. if some one can help...

---

### Post by Ramses de Norre on 2007-03-11
1) Make the new partition and mount it at e.g. /media/var

2) Copy everything from /var to /media/var, you can do so with these commands: ```
cd /var
find . -depth -print0 | cpio &#8211;null &#8211;sparse -pvd /media/var/
```

3) Modify fstab and enter this line for /var: ```
/dev/???    /var     ext3    defaults,nodev,nosuid,noexec        0       2
``` Fill in the right device node instead of "???".

4) Reboot, otherwise your logs will be totally out of sync.

---

### Post by prince_niceguy on 2007-03-12
what about the space taken by my previous var directory? will it be restored ... if not how do i do it???

---

### Post by Ramses de Norre on 2007-03-12
Ow correct, before the reboot you need to do ```
sudo mv /var /var.bak
```
Then after a while when you're sure everything works ok you can just delete that directory.
Sorry I forgot about that step.

---

### Post by prince_niceguy on 2007-03-12
thanks...a ton..

now i have got good amount of free space on my root partition... thank you so much...

---

### Post by prince_niceguy on 2007-04-18
now there is a strange problem coming mount /var/lock not found. I am using feisty... not sure why it is coming though... there is a folder lock under var but it has to be mounted??? any one any idea?

---

### Post by Ramses de Norre on 2007-04-18
/var/lock is just a regular directory here... With permissions drwxr-xr-x and owned by root:root. This is on Arch but I guess it will be the same on ubuntu.

---

