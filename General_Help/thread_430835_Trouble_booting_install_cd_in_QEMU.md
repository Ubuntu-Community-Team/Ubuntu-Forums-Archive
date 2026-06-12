---
title: "Trouble booting install cd in QEMU"
date: 2007-05-02
forum: General Help
---

### Post by vgdx7 on 2007-05-02
I've installed QEMU and I'm trying to boot my XP install CD with the command:

qemu -boot d -cdrom /dev/cdrom -hda hd.img

The problem is my CD drive isn't working so I need to use my DVD drive, cdrom0, but I can't seem to change the above command to make this change?

---

### Post by joft on 2007-05-02
Hmmm, what do you mean by "can't change"?

You could use the real device node of your DVD drive e.g. /dev/hdc or /dev/hdd or whatever instead of the symbolic link /dev/cdrom.

---

### Post by vgdx7 on 2007-05-02
I migrated form Vista about a two months ago and I'm still working on linux command line and file systems. I meant that by tweaking the command with a different drive name I still couldn't get Qemu to find the cdrom0 location. For instance I replaced the drive locations you listed but when I ran it, it still booted my cd drive rather then my dvd drive. For instance would the command line look like this?
qemu -boot d -hdd /dev/hdd -hda hd.img
 thanks

---

### Post by joft on 2007-05-02
qemu -boot d -hdd /dev/hdd -hda hd.img

does the following:
qemu is instructed to emulated 2 device: a IDE slave device on the 2. emulated IDE controller ("-hdd") and a IDE master device on the 1. emulated IDE controller ("-hda").
The emulated hda will use "hd.img" as its contents and the emulated hdd will use the physical device /dev/hdd (whatever this is on your computer) as its "contents".
But - since you don't specify option "-cdrom", qemu emulates another device (IDE master on 2. controller = hdc) which points to physical /dev/hdc on your host. And now, if you say, it still boots your CD-ROM drive, /dev/hdc on your computer seems to be the device node of your CD-ROM drive.

So:
1. Find out which device node is used by your DVD drive, e.g. by looking at the output of:
```

ls -l /dev/disk/by-id

```
You should see a kind of association between ID strings (of hardware) and device node names.
2. Use
```

qemu -boot d -cdrom /dev/XXX -hda hd.img

```
and replace "XXX" with the device node's basename used by your DVD drive. Since /dev/hdc  seems to be your CD-ROM drive (see above), your DVD drive could be e.g. hdb (1. IDE controller, slave) or hdd (2. IDE controller, slave).

---

### Post by vgdx7 on 2007-05-02
That was it.

Thanks for your excellent help.

---

