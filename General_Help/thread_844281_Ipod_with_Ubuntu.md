---
title: "Ipod with Ubuntu"
date: 2008-06-29
forum: General Help
---

### Post by fraggle09027 on 2008-06-29
I recently bought a I-pod on ebay. Once I received it I had no problem setting it up with gtkpod and even transfered music and video to it. Now however something changed and when I try to move a file to it or unmount it I get an error.

When trying to copy:
Error opening '/media/iPod/iPod-control/Music/F47/gtkpod631398.mpg' for writing (permission denied)

I tried to change ownership (chown) and permissions (chmod) and I even tried to copy in the shell as root but all no good.

root@Fraggle2:/media/iPod/iPod_control# chown cgilbert /media/iPod/iPod_control/Music
chown: changing ownership of `/media/iPod/iPod_control/Music': Operation not permitted


Any Ideas?
__________________

---

### Post by Rocket2DMn on 2008-06-29
You cannot use chown and chmod on an ipod because it is not formatted with a linux filesystem - it probably uses FAT32 or FAT16.  You can mount from the terminal using umask=000 or uid=1000 as an option with the mount command.  Normally, you should be able to plug the ipod in and it should automount with read/write permissions.  You won't want to use the mount command every time you plug in the ipod.

Try ejecting the ipod, waiting a few seconds, then plugging it back in.  If it isn't working, please post
```
sudo fdisk -l
mount
cat /etc/fstab
sudo blkid
```

---

