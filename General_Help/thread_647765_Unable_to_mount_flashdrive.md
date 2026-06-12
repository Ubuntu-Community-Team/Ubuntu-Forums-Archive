---
title: "Unable to mount flashdrive"
date: 2007-12-22
forum: General Help
---

### Post by stoneage on 2007-12-22
I tried to change the mount point for a flash drive by right-clicking and entering /mnt/ATTACHE in the volume section and now I get an error message:-

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR(usually/)

Fair enough, but how do I correct the error if the drive cannot be mounted ?

Oops

---

### Post by cmnorton on 2007-12-22
**This post could be related to an Ubuntu bug filed at**: [https://lists.ubuntu.com/archives/ubuntu-bugs/2007-March/431323.html](https://lists.ubuntu.com/archives/ubuntu-bugs/2007-March/431323.html) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This might be a bug. 

If the origin of this flash drive is Windows, mount it there and change the volume name.

---

### Post by stoneage on 2007-12-22
Really ? I thought it was stupidity.
I used it originally to transfer files from a windows machine I can try it in a day or two. 
Can I treat like changing a filename - right click and rename ?

Thanks.

---

### Post by stoneage on 2007-12-23
Problem solved:

sudo mount /dev/sdb1 /mnt/ATTACHE

Thank you.

---

