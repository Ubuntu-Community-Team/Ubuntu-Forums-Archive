---
title: "Move File from LiveCD Desktop to HD with Terminal"
date: 2006-10-13
forum: General Help
---

### Post by msabers on 2006-10-13
In order to install Ubuntu on my Mac Mini, I have to copy a file called lilo.conf to the hard drive that Ubuntu was installed on. The folder is on my Live CD desktop, and I want to move it to /mnt/ubuntu/etc with a chrooted terminal. How do I do this?

---

### Post by aysiu on 2006-10-13
Wouldn't it be ```
sudo mv ~/Desktop/lilo.conf /mnt/ubuntu/etc
```? Or you could just press Alt-F2 and type ```
gksudo nautilus
``` Are you using a PowerPC or Intel Mac Mini?

Are you sure you need to copy lilo.conf over...?

---

