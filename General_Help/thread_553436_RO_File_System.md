---
title: "RO File System"
date: 2007-09-17
forum: General Help
---

### Post by Reonarudo on 2007-09-17
Ubuntu is auto mounting my external drive as ReadOnly and its simply fat32, its strange cause it worked perfectly 'till now... help pls

---

### Post by southernman on 2007-09-17
If you run this in a terminal...
> 
gksudo gedit /etc/fstab

go to  the line pertaining to your external drive you'll see "ro" on that line. changing it to read as "rw" **should** solve your problem.

If your not sure which line is for your external drive after running the above command just copy and past the file here so we can help you out.

---

