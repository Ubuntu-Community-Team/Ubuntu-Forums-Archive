---
title: "Unable to see windows partition- Installed via wubi on same drive"
date: 2008-05-25
forum: General Help
---

### Post by Sims12345 on 2008-05-25
I have installed ubuntu 8.04 using wubi onj the same harddrive and cannot see the windows partition...? How do I see it and then read and write to it?


PS. I am running windows vista

Thanks,

Simon

---

### Post by Zoja on 2008-05-25
Try typing sudo fdisk -l , you'll see your partitions in terminal

---

### Post by Sims12345 on 2008-05-25
Ok, so I can see them in the terminal but how am i able to read and write to them?

---

### Post by Zoja on 2008-05-26
put the output of sudo fdisk -l here

---

### Post by lswest on 2008-05-26
usually WUBI installs mount the host partition (the windows partition) as /host/  try looking there.

---

### Post by Sims12345 on 2008-05-27
Sorry for the delade response, i have been really busy. I was going to go and type in the command and compy the output but I have now run into a new problem. See here

[http://ubuntuforums.org/showthread.php?p=5056918#post5056918](http://ubuntuforums.org/showthread.php?p=5056918#post5056918)

---

### Post by knutschr on 2008-05-27
It seems like the newest kernel will not work for you.
When starting, have you the option to start another kernel?
If so, do that.

---

### Post by Sims12345 on 2008-05-27
No, after i select ubuntu from the boot menu, it loads up and just before the login menu, it gives me that error and it wants me to type commands, it looks like this:

(initramfs)_

---

