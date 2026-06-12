---
title: "mounting new hard drives"
date: 2007-09-30
forum: General Help
---

### Post by itlarson on 2007-09-30
As a way of transferring data, I installed a hard drive in one computer, formatted it ext3, loaded it up, and moved it to another computer.  But now I cant get it to mount so that I can read it.  I tried to config it using the tool in the k menu, the drive showed up there, but trying to set it up just created a new directory on the other drive, instead of mounting the drive there.  I tried re- installing kubuntu, but it wouldn't let me uncheck the format check box- so I didn't proceed.

---

### Post by WakkaDojo on 2007-09-30
Linux has a root mount point, and every other file system mounted afterwards is in the tree, hence you can't have two mount points as in windows (like C:\ and D:\ ; there's only /). So you can mount it in /media/* or /mnt/* or whatever you want, but it can't be at the beginning.

---

