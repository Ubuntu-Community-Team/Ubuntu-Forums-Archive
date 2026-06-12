---
title: "DAR error Cannot add absolute path"
date: 2008-04-26
forum: General Help
---

### Post by Barry53 on 2008-04-26
I'm trying to use DAR (Disk Archive). I have followed a mini how-to. My command line is:
```
DIR=/backup
FILE=${DIR}/`/bin/date -I`_full
/usr/bin/dar -v -m 256 -y -s 700M -D -R / -c $FILE -Z "*.gz" -Z "*.bz2" -Z "*.zip" -Z "*.png" -P /backup -P /cdrom -P /dev -P /intrd.img -P /lost+found -P /media -P /mnt -P /proc -P /sys -P /tmp
```

The error I get is:
> Parse error on command line (or included files): Cannot add an absolute path /backup/2008-04-26.1.dar is required for further operation, please provide the file. [return = OK |Esc = cancel] Can anyone see where I've gone wrong?

Thanks in advance.

---

### Post by Barry53 on 2008-04-26
I have found the answer. I removed the '/' in each of the -P options and it worked fine. The command is now:
```
/usr/bin/dar -m 256 -y -s 700M -D -R / -c $FILE -Z "*.gz" -Z "*.bz2" -Z "*.zip" -Z "*.png" -P backup -P cdrom -P dev -P intrd.img -P lost+found -P media -P mnt -P proc -P sys -P tmp
``` 
Hope this helps someone else.
Cheers

---

