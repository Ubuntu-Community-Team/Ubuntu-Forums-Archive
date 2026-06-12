---
title: "Root user cd installation not working"
date: 2005-06-24
forum: General Help
---

### Post by Malpin on 2005-06-24
Hellow, I am new to linux so you might see me here often.

I am curently trying to install ut2004, but when i go to the termina, switch to the root user and try to install it i get this message.

root@cpe-70-114-146-248dustin:/home/dustin # /media/cdrom0/linux-installer.sh
bash: /media/cdrom0/linux-installer.sh: /bin/sh: bad interpreter: Permission denied

can someone please tell me how to fix this, i am also sorry if this is in the wrong section of the forums but it seemed to fit in 3 different ones.

---

### Post by nictuku on 2005-06-24
That may happen when you try to run something from a non-linux filesystem, like a CD-ROM's is9660.

Copy the contents of the CD into a folder and run it from there:

# mkdir ~/ut2004install
# cp -R /media/cdrom0/*  ~/ut2004install
# cd ~/ut2004install ; ./linux-installer.sh

Good luck!

---

