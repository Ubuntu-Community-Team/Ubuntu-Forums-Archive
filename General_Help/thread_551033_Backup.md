---
title: "Backup"
date: 2007-09-14
forum: General Help
---

### Post by hojjat on 2007-09-14
I was just thinking that, it would be grate to be able to have a backup of the core files of linux (those needed by linux to start up correctly). This way, I could make sure, if I did something that makes Ubuntu to crash, I can restore it easily. Something like a drive image could help, but not an image of total drive (which inclues /home directories too), only the core parts. Is this available? And is there a best practice for it? For example, do you suggest a special backup software?

By the way, I'm running Feisty on a virtual machine.

---

### Post by tszanon on 2007-09-14
> **hojjat said:**
> I was just thinking that, it would be grateful to be able to have a backup of the core files of linux (those needed by linux to start up correctly). This way, I could make sure, if I did something that makes Ubuntu to crash, I can restore it easily. Something like a drive image could help, but not an image of total drive (which inclues /home directories too), only the core parts. Is this available? And is there a best practice for it? For example, do you suggest a special backup software?

By the way, I'm running Feisty on a virtual machine.
If you know what files are necessary, you could just tar them. Or tar+gzip.
Since I have a seperate /home, it's viable to create a partition image using partimage.

---

### Post by por100pre1 on 2007-09-14
If you have an external hard disk drive, you can use grsync to backup your home folder. This method is convenient because after its first use, grsync can be setup to just synchronize the folders for a really quick backup.

---

### Post by hojjat on 2007-09-15
I don't want to backup /home indeed. I want to backup directories like /bin and /etc and others that are needed for the operating system to work well. And I want to back them up in a way that restoring them would simply make the OS come back to health.

Anwyays, is there a way to create a partition and move the "/home" folder to it?

---

### Post by tszanon on 2007-09-16
> **hojjat said:**
> I don't want to backup /home indeed. I want to backup directories like /bin and /etc and others that are needed for the operating system to work well. And I want to back them up in a way that restoring them would simply make the OS come back to health.

Anwyays, is there a way to create a partition and move the "/home" folder to it?
I'm not sure, but I think there are some files in /home that are needed for you to login.

Moving /home to a new partition seems to be easy, but I strongly suggest that you create a new thread asking how to do it. I may be forgetting important things when I say that you only need to:
1. create the new partition;
2. copy /home to the new partition;
3. edit /etc/fstab to mount the new partition under /home.

---

### Post by dpar on 2007-09-16
Here's a read on creating a seperate home partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

