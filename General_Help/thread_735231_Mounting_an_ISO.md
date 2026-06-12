---
title: "Mounting an ISO"
date: 2008-03-25
forum: General Help
---

### Post by KrGAce on 2008-03-25
In Windows land, either Alchol-soft (120%) or Nero allowed me to mount an ISO, and thus browse the files of that ISO, or whatever.  Is there a Linux software equivalent?

Many thanks in advance,


AceMan

---

### Post by zxan on 2008-03-25
> **KrGAce said:**
> In Windows land, either Alchol-soft (120%) or Nero allowed me to mount an ISO, and thus browse the files of that ISO, or whatever.  Is there a Linux software equivalent?

Many thanks in advance,


AceMan

In Linux or Ubuntu u can use the terminal to mount a iso as CD-rom with these commands:
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso
```

GMount-Iso you can also mount a iso.

GIsoMount you can mount, browse and burn isos.

[CDemu]("http://cdemu.sourceforge.net/") you can mount isos CD/DVD drive emulator for Linux.

---

### Post by x1a4 on 2008-03-25
Here you go:
```
mount -o loop -t iso9660 /path/to/file.iso /mount/point
```

Once you do this you will be able to access the /mount/point directory (or whatever other directory you mounted the iso on) as if it were another directory with files on your system.

EDIT: to mount the iso each time you boot:
In your /etc/fstab file add the following line: 
```
/path/to/file.iso /mount/point iso9660 ro,loop=/dev/loop# 0 0
```
The # in /dev/loop# is a number from 0 to 7.  That's how many loop devices are made by default so you can mount up to 8 iso images.  If you want more, create more loop devices.

---

### Post by KrGAce on 2008-03-25
Many thanks!  I knew Linux was cool for a reason.


Again, my thanks!


AceMan

---

### Post by marcusfurius on 2008-05-14
You could try [this application]("http://www.marcus-furius.com/?page_id=14"). It is designed specifically for Ubuntu, installs via a deb installer, has a simple to use GUI and mounts ISO, IMG, BIN, MDF and NRG Images, and doesn't require a password to mount images.

---

