---
title: "Mount new partiton"
date: 2007-02-15
forum: General Help
---

### Post by scottsanpedro on 2007-02-15
Hi,
I have just created a new 3gb partition with gparted.
When I reboot I want to name that partiton mydocuments and use it to store bits so its there on a upgrade or reinstall.
the partition is hda4
how do i mount this?
thanks
Scott

---

### Post by charl.ie on 2007-02-15
```
sudo mount /dev/hda4 /media/mydocuments
```

if you want it to mount on startup, you will have to edit fstab

To unmount:
```
sudo umount /dev/hda4
```

---

### Post by scottsanpedro on 2007-02-15
sorry to sound stupid, fairly new to all this.
Presumably I can mount this to any location I want.
Is off media the best place, especially for when I upgrade etc.
also I've not dealt with fstab before.
many thanks again.Scott

---

### Post by charl.ie on 2007-02-15
Those commands will only mount it temporarily (aka it won't be mounted after re-boot), and yes, you can mount it anywhere you want. I prefer to use /media, as that is where the cdrom and stuff is mounted by default.

If you want it to be mounted on boot, you need to add a line to /etc/fstab, in this format:
```
/dev/harddrive   /mount/point   filesystem  defaults    0           0
```

So yours might look like
```
/dev/hda4    /media/mydocuments  ext3      defaults    0        0
```

I'm not too sure about the last two 0's

**[COLOR="Red"]Warning:[/COLOR] Remember to back up fstab before editing it: sudo cp /etc/fstab /etc/fstab_backup**

---

### Post by scottsanpedro on 2007-02-15
hey..thanks for that. works beautifully. cheers

---

### Post by scottsanpedro on 2007-02-15
sorry.me again.
I tried to add files to this folder/drive but presumably the permissions aren't correct.
I tried chown to my log in name and doesn't seemed to have help.
sorry to be a pest
Scott

---

### Post by scottsanpedro on 2007-02-15
sorry..ignore me
I had to create directories below. thanks..i'll go away now :)

---

