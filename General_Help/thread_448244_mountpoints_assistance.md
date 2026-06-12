---
title: "mountpoints assistance"
date: 2007-05-18
forum: General Help
---

### Post by jazzor on 2007-05-18
How do I find the device from a mountpoint the correct way (ie not using text processing hacks (sed, awk) ) in bash?

eg: /mnt/usbdrive is a mountpoint and /dev/sdc is my usb...what do i need to write in the script file to get /dev/sdc given /mnt/usbdrive?

If text processing is really required then it must work on mountpoints that dont contain the device name in them...

---

### Post by madoka on 2007-05-19
Have you tried the df command?  Granted, its output is somewhat tricky to parse.

---

### Post by thelinuxguy on 2007-05-19
> **jazzor said:**
> what do i need to write in the script file to get /dev/sdc given /mnt/usbdrive?


This statement in a script seems to work. The script accepts the mount point as the first parameter.
```

echo `mount | grep "$1 " | cut -d' ' -f1`

```

Extra space after $1 will avoid dual matches (see Stephen Howard's post below). For mount points with spaces, use quotes as in 
```

./devicefrommountpoint.sh './Desktop/mount point' 

```

This may need some correction to work for all cases. And besides, since you want to avoid text hacks, I am not sure this is what you want. But this seems to work.

---

### Post by Stephen Howard on 2007-05-19
thelinuxguy's script is good but would fail if there's two mount points with the same characters.  For instance, /usr and /usr/local would match for both.  To stop a dual match you only need to append a space to the mountpoint string:

echo `mount | grep $1" " | cut -d' ' -f1`

alternatively:

grep $1" " /etc/mtab | awk '{ print $1 }'  


or

grep $1" " /etc/mtab | cut -d' ' -f1

---

### Post by thelinuxguy on 2007-05-19
> **Stephen Howard said:**
> To stop a dual match you only need to append a space to the mountpoint string:

echo `mount | grep $1" " | cut -d' ' -f1`


Thanks. I had overlooked that. Edited my post above to include this. $1 should be within the quotes to account for mount points with spaces.

---

