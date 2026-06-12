---
title: "login problem"
date: 2007-12-21
forum: General Help
---

### Post by yesongs on 2007-12-21
I'm a complete newbie in ubuntu and Linux, and I have some problems after the last update.
the entry in menu.lst that points to the disk I have installed ubuntu is normally hda(0,0)
after the update I noticed (booting with liveCD) that this entry is changed to hda(2,0).
Now my problem is here:
How can I get the permission to change menu.lst since I boot from liveCD?:?:?

---

### Post by taurus on 2007-12-21
You need to mount the partition where / is(or /boot if you have a separate partition for /boot).  Then, you can edit your menu.lst on the harddrive.  

Assuming it's /dev/hda1, run

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
gksudo gedit /mnt/ubunut/boot/grub/menu.lst
```

---

### Post by yesongs on 2007-12-21
I have my Ubuntu Back!!!
Thanks a lot!!\\:D/

---

