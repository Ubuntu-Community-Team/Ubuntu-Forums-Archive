---
title: "need to make iso image from a cd..."
date: 2007-08-28
forum: General Help
---

### Post by Mia_tech on 2007-08-28
I have a live cd of ubuntu and I would like to make an iso image and put it on my hard drive so I can bootup with vmware..........someone could help me how to make this happen.

---

### Post by kuja on 2007-08-28
will vary depending on your cd drives device, but ....
dd if=/dev/hda of=$HOME/ubuntu.iso

---

### Post by Mia_tech on 2007-08-28
no I tried that and this is  what I gott


jorge@ubuntu-box:~$ dd if=/media/cdrom0 of=/home/jorge/navynos.iso
dd: reading `/media/cdrom0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000773459 seconds, 0.0 kB/s

---

### Post by kuja on 2007-08-28
You can't use the mount point, you need to use the device node, which will be /dev/something

/dev/cdrom may work, otherwise it will be /dev/hd[a letter between a and h)

---

### Post by capink on 2007-08-29
1. install mkisofs

```
sudo apt-get install mkisofs
```

2. Make sure the cd is mounted

3. make the iso:

```
sudo mkisofs \
    -o isofilename.iso \
    -b isolinux/isolinux.bin \
    -c isolinux/boot.cat \
    -no-emul-boot \
    -boot-load-size 4 \
    -boot-info-table \
    -r \
    -V "Ubuntu Live CD" \
    -cache-inodes  \
    -J \
    -l \
    /path/to/cdrom/mount/point
```

---

### Post by gletob on 2007-08-29
how about right clicking the cd on the desktop>copy disc>change copy disc to file image>write

---

### Post by Mia_tech on 2007-08-29
thanks all for the help, I tried both and genisoimage game some problems, but dd if=/dev/cdrom of=/home/isoname.iso.........did it for me.

---

### Post by komputes on 2007-12-07
This works for me:

```

sudo umount /dev/cdrom
dd if=/dev/cdrom of=/home/username/image.iso

```

I think you need to unmount (sudo umount) the device before you make an image of it. afterwards if you want to mount the cd back onto the desktop, do:

```
sudo mount /dev/cdrom
```

If you want to mount the image file (image.iso) do this:
```

sudo mkdir /media/iso
sudo mount -t iso9660 -o loop image.iso /media/iso
```

Hope this helps :p

---

### Post by Mia_tech on 2008-02-08
why would you want to mount an iso image....

---

### Post by kuja on 2008-02-08
> **Mia_tech said:**
> why would you want to mount an iso image....

One good example would be with the (k)ubuntu iso. I'd rather just rip it, mount it, and set it up in the sources.lst then bother with the disk. Sure, you could just extract it ... but why bother when you can just mount it anyway with zero hassle?

---

### Post by Mia_tech on 2008-02-08
yeah I understand your point but with this code your not mounting the cdrom... you are mounting the image file .... my question is why would you mount the .iso image... I don't know maybe I didn't understand what you said... or I'm missing something

sudo mkdir /media/iso
sudo mount -t iso9660 -o loop image.iso /media/iso

---

### Post by kuja on 2008-02-08
> **Mia_tech said:**
> yeah I understand your point but with this code your not mounting the cdrom... you are mounting the image file .... my question is why would you mount the .iso image... **I don't know maybe I didn't understand what you said... or I'm missing something**

sudo mkdir /media/iso
sudo mount -t iso9660 -o loop image.iso /media/iso

Looks that way.

What I'm saying is you make an image of the CD so you don't have to use the CD anymore. Finding/inserting the CD can be tedious, and on top of that transferring from the CD-ROM is very, very slow, especially when compared to the speed of the hard drive.

---

### Post by forrestcupp on 2008-02-08
You can use K3B, which is one of the best CD/DVD copying/burning  apps I've seen.  Make sure your CD is mounted, and in K3B go to Tools->Copy CD.  In the window that comes up, check the box that says 'Only Create Image'.  In the 'Image' tab, you can set the directory to save the image to.

```
sudo apt-get install k3b
```
It will install KDE libs, though.  But it's worth it.

---

