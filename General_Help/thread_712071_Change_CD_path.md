---
title: "Change CD path"
date: 2008-03-01
forum: General Help
---

### Post by HanDy_man on 2008-03-01
How to change the path to the CD? The default is /media/cdrom but want it to be /home/handy/virtual-drives/1. In the terminal I've try CDPATH= , set cdpath , export CDPATH and than I start the program which needs to read from the virtual CD but it still says to mount CD.

---

### Post by pointone on 2008-03-01
Why not just make a symlink?

```
ln -s /media/cdrom /home/handy/virtual-drives/1
```

---

### Post by HanDy_man on 2008-03-01
> ln: creating symbolic link `/home/handy/virtual-drives/1/cdrom' to `/media/cdrom': Function not implemented

I realy don't want to swich back to Windowz...

---

### Post by HanDy_man on 2008-03-01
Hm I've use "Generic Mount" (AcetoneISO2) to mount iso in cdrom but still doesnt work. It seems that i need the original disc.

Thanks for reply  anyway.

---

### Post by Gillingham on 2008-03-01
Do you need to edit the /etc/fstab file or remount the drive?  I think the command would be  mount but you would want to google / use the man pages to get more details of the syntax.

David

---

