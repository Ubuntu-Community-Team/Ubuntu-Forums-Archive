---
title: "shell script on fat32 partition"
date: 2008-01-04
forum: General Help
---

### Post by motoperpetuo on 2008-01-04
I have a shell script that i run on a fat32 partition, usually from the GUI. It was working fine before I altered fstab to mount the fat32 partition automatically. Now when I double click on the icon for the shell script, it just opens in gedit. When I try to run it from a command line, it says "command not found."

I tried running this:

       sudo chmod a+x shellscript.sh

also to no avail. Is there something about my partition mounting automatically that would make my lose the ability to run a shell script? It seems like the file somehow lost it's executable attribute, but I don't know how to restore it (or how to check that, exactly).

---

### Post by taurus on 2008-01-04
How do you mount it from /etc/fstab?

```
cat /etc/fstab
```

---

### Post by motoperpetuo on 2008-01-04
/dev/sda4 /media/ddrive vfat user,auto,fmask=0111,dmask=0000 0 0

(I just pasted this out of a how to page I found somewhere here...I don't really understand the parameters after "vfat".)

---

