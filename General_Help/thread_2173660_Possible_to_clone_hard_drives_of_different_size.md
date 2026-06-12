---
title: "Possible to clone hard drives of different size?"
date: 2013-09-10
forum: General Help
---

### Post by davethewave83 on 2013-09-10
I have a 1Tb hard drive with Ubuntu installed, and a 250Gig drive which I would like to use to clone the 1Tb

the 1Tb is not exceeding 250Gb in used space. I understand I could simply copy the files over from a boot CD, but this has in the past messed up my permissions and rendered the partition unbootable due to the fact the UUID changes, so there's a lot of work to fix this in the fstab etc. 

If the two drives were identical in size, I could use DD to clone, unfortunately this is not the case. 
is there any way to achieve the same goals of cloning with DD (maintaining UUID/Permissions etc) when limited space is available on the backup drive?

---

### Post by tgalati4 on 2013-09-10
This is a risky proposition.  You could shrink the partition on the 1TB drive to 249GB then clone, but that entails some risk as well.  I would just backup personal data to the 250GB drive, and not bother with the clone on that drive.  If you really need to clone, then buy another similar make/model 1TB drive and clone that.  You still need to repair UUID's to make it bootable, no way around that.

---

### Post by VMC on 2013-09-10
Are you just wanting to use the 256gb drive as a backup of the 1tb drive? If so then, several options available - Clonezilla, partclone or fsarchiver.

edit:do you want/need to clone the entire drive or just partitions?

---

### Post by SuperFreak on 2013-09-10
[http://redobackup.org]("http://redobackup.org") might do this. I have backed up my OS and other partitions with this but have not yet tried restore . I t will copy the used portion of the disk to a somewhat compressed copy. Believe it works using the same code as Clonezilla but is simpler to use

---

### Post by VMC on 2013-09-10
> **SuperFreak said:**
> [http://redobackup.org](http://redobackup.org) might do this. I have backed up my OS and other partitions with this but have not yet tried restore . I t will copy the used portion of the disk to a somewhat compressed copy. Believe it works using the same code as Clonezilla but is simpler to use
Yes, redobackup is just a front-end to partclone., and partclone is easy to use. Example:
Clone Partition #6 of sda drive, use gzip to compress (-N is the curses for partclone, brings up a guid window):
```
sudo ./partclone.ext4 -N -c -s /dev/sda6 | gzip --fast>/media/<whatever>/ubuntu.gz
```

---

### Post by ibjsb4 on 2013-09-10
> **tgalati4 said:**
> You could shrink the partition on the 1TB drive to 249GB then clone, but that entails some risk as well.

That is what I would have to do with clonezilla.

---

