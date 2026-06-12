---
title: "mount filetype issue - remote share not in host.dir format"
date: 2020-05-09
forum: General Help
---

### Post by hbackus on 2020-05-09
I have a software install CD for an OpenVMS system. I am trying to read the files on it on USB CDROM player attached to my Linux PC by USB. 
The reason for trying to read it on my Linux PC is the original support manuals have been lost and copies of the manuals in PostScript are on the CDROM disk.

lsusb shows the USB CDROM device.
When I try to mount the CD to read I get the message “…remote share not in ‘host:dir’ format…”

I have tried:

sudo mount –t nfs   /dev/cdrom  /mnt
sudo mount –t nfs4  /dev/cdrom  /mnt 
sudo mount –t auto  /dev/cdrom  /mnt
sudo mount  –t iso9660  /dev/cdrom  /mnt

Any assistance on syntax or why I can't mount the CD for reading would be appreciated.
;)

---

### Post by CelticWarrior on 2020-05-09
Any optical media is typically mounted automatically.
Which release/version is that "Linux PC"?

---

### Post by hbackus on 2020-05-09
Ubuntu 18.04.4
Looks like the issue is the file system on the CD and not how Linux is trying to mount.

---

### Post by lvm on 2020-05-10
VMS uses proprietary ODS aka files-11 filesystem, you have to find drivers. No idea if they exist.

---

### Post by hbackus on 2020-05-11
Thanks.

---

### Post by hbackus on 2020-05-11
Thanks

---

### Post by hbackus on 2020-05-11
I think you right. finding drivers for Files-11 would be a challenge.

---

