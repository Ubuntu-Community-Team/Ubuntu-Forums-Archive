---
title: "Another Hard Drive Permission problem"
date: 2007-09-13
forum: General Help
---

### Post by caramelsoul on 2007-09-13
I have been using Feisty for a few months now in a dual boot system with windows and been happy with the preformance of Ubuntu so much so that i wanted to get rid of Windows all together. 

I have four internal hard drives in my system. Two are IDE and two are SATA.

I reinstalled Ubuntu over my windows hard drive then reformatted the drive i originally had Ubuntu on to Ext3. I left my other two drives which are NTFS formatted as they were for the time being as they have media on them that i want to keep, like films, music and photos.

I can mount the drives that are NTFS but i cant write to the one that is formatted to Ext3. Do i have to do something with the flags?

Can someone help to put me out my misery please.

---

### Post by prince_niceguy on 2007-09-13
Just to understand better the hard drive with ext3 is the disk with ubuntu installed or it is just a storage device?

if it is the one with ubuntu installed then it is by design that it is not allowing you to write as only root can write on the root folder.

If it is a data storage then what you need is to add following flags in fstab

> /dev/hdb1 /mnt/hdb1 ext3 rw, 1 1

further refer to this thread. will help understanding and configuring better.

[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by caramelsoul on 2007-09-14
Thanks for the links mate.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) is exactly what i needed. Im a happy man now. :)

---

### Post by hotweiss on 2007-09-29
Thanks that linked helped me to finally get my ext3 drive working. I'm trying to migrate from NTFS.

---

