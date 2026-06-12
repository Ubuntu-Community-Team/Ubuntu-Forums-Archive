---
title: "UDEV rules &amp; truecrypt"
date: 2007-09-14
forum: General Help
---

### Post by thirddeep on 2007-09-14
Hi all ...

First time post here, so excuse any n00bness :-)

I wanted to create a UDEV rule and script so when I plugged in my USB keyring :
1) Mount the truecrypt volume
2) Backup my files
3) Unmount the truecrypt volume
4) Still have gnome pop up the file browser

Now, all this works with one minor problem.  After the script is done, the data that was copied over, is also in the underlying directory.  A bit hard to explain, so here is the code :

UDEV rule :
```
ATTRS{serial}=="A76000000000004", ATTRS{product}=="Flash Voyager", ATTRS{manufacturer}=="Corsair", SYMLINK+="usbbackup", RUN+="/usr/bin/usb_backup.sh"
```

Script :
```
#!/bin/sh

HOME=/home/xxx
MOUNT=/mnt
TARGET=/home/xxx/usb
OUTPUT=backup.out

mount /dev/usbbackup /mnt > $HOME/$OUTPUT 2>&1
/usr/bin/truecrypt $MOUNT/backup.dat $TARGET -p blablabla >> $HOME/$OUTPUT 2>&1

cp -r /home/xxx/Documents $TARGET >> $HOME/$OUTPUT 2>&1

/usr/bin/truecrypt -d $TARGET >> $HOME/$OUTPUT 2>&1

umount $MOUNT >> $HOME/$OUTPUT 2>&1

```

So, documents is copied over, truecrypt unmounts and then ... those copied files is ALSO in /home/xxx/usb.  I tested, and the files is in the truecrypt volume.

What am I missing ? :-)

---

