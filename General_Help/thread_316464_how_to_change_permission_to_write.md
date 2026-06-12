---
title: "how to change permission to write"
date: 2006-12-10
forum: General Help
---

### Post by akramIT on 2006-12-10
I got this error when i copy to hda1 which i mount by root and the owner of it and i cann't copy anything to ntfs partition

Error while copying to "/media/hda1/"
You do not have permissions to write to this folder.

so how can i gain write permssion to /media/hda1 ?

thanks in advance

---

### Post by aysiu on 2006-12-10
NTFS is generally read-only in Linux unless you feel like using some experimental software.

---

### Post by akramIT on 2006-12-11
ok ,so what is the software to use to make me write on ntfs partition?

---

### Post by aysiu on 2006-12-11
> **akramIT said:**
> ok ,so what is the software to use to make me write on ntfs partition?
Try this:
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by akramIT on 2006-12-11
i got the solution at last

i now unmount the /dev/hda1

then mount it with ntfs-3g and now i have permission to write in my ntfs partition

but i still one more option is activate the left click to let me creat folder and so on

i still don't know how

any clue guys

---

