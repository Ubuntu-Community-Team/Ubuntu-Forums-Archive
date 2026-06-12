---
title: "trouble booting ubuntu server 16.04.2"
date: 2017-08-03
forum: General Help
---

### Post by ehab238 on 2017-08-03
Hello,


I just finshed installing ubuntu server 16.04.2 last night, but it was stuck on this check; /dev/sda1: clean, 66048/9707520 files, 1015209/38812416 blocks .
i left it for the night but still it was stuck on the same check this morning so i did a reboot but it did not help. then i tryed this [https://askubuntu.com/a/882960](https://askubuntu.com/a/882960) but this also didn't help so i was wondering can someone help me 



Kind regards

Ehab238

---

### Post by BenginM on 2017-08-03
Hiya , welcome to the forums ..

so, what are the results of step one and two from that link ..

and the outputs of free -h, and swapon -s, df -h

also did you boot with a specific kernel boot parameter ..!

---

### Post by ehab238 on 2017-08-03
Hey,
 here are the results.

[https://ibb.co/jujk9v](https://ibb.co/jujk9v)
[https://ibb.co/hT5spv](https://ibb.co/hT5spv)
[https://ibb.co/gx2u2F](https://ibb.co/gx2u2F)
the last one is in dutch i can translate it

step 1 check of the inodes, blocks and sizes
step 2 check of the directory structure
step 3 check of the connection between the directory
step 4 check of the  Reference numbers
step 5 check of the Group summaries

/dev/sda1:66048/9707520 files (0.2% Not continuous), 1015312/38812416 blocks


and then i reboot and its again stuck

---

### Post by ehab238 on 2017-08-03
HA i found a way around if i try to boot in "safe mode" and then hit resume it works

---

### Post by BenginM on 2017-08-03
Ok, try to preform the file system check in  (safe) recovery mode , 

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

drop to a root shell, and run:

mount -o remount,rw /
fsck -f
mount -o remount,ro /
sync
reboot

---

### Post by ehab238 on 2017-08-03
it works thank you verymuch :D

---

### Post by BenginM on 2017-08-03
Excellent , well done. :)

---

