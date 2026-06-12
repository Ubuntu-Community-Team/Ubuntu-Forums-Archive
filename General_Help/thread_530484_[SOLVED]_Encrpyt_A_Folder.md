---
title: "[SOLVED] Encrpyt A Folder"
date: 2007-08-20
forum: General Help
---

### Post by donut2790 on 2007-08-20
Anyone know a good program to encrypt a folder?  I tried using xarchiver and and Fileroller but I can't seem to set a password on the folder  :confused:

---

### Post by kellemes on 2007-08-20
Will this do?
Never tried it myself..

[http://www.tuxforums.org/forum/viewtopic.php?t=532]("http://www.tuxforums.org/forum/viewtopic.php?t=532")

---

### Post by mbeierl on 2007-08-20
From what I know there is no easy way to encrypt just a portion of a filesystem.  The easiest answer I can think of is to mount an encrypted filesystem at that folder's location.

I do not use encrypted FSs, but the general idea is as follows:

1) create a file to hold your directory.  For example, if you want to be able to hold 1gb of data, your file must be 1gb
2) format the file as an encrypted filesystem
3) add the entry for the filesystem to /etc/fstab

Edit: This is what the above post explains clearly.

The problem that I would see with this approach is that all processes that have read access to the directory get to read the filesystem once it is mounted - in other words the password is only used for attaching the directory, not for protecting each file at access time.

---

### Post by donut2790 on 2007-08-20
Thank you! But I was hoping for something with a GUI actually. Hmmmmm, anyone know?

---

### Post by bodhi.zazen on 2007-08-20
Have you looked at seahorse ?

[http://www.gnome.org/projects/seahorse/](http://www.gnome.org/projects/seahorse/)

Also check this out :

[http://www.tuxforums.org/forum/viewtopic.php?t=532](http://www.tuxforums.org/forum/viewtopic.php?t=532)

---

### Post by chrisccoulson on 2007-08-20
Yes, Seahorse does it for me. It integrates with Nautilus to give you an 'Encrypt' option in the context menu. If you choose to encrypt a folder, it gives you the option of encrypting files individually, or packaging them in an archive and encrypting it.

---

### Post by donut2790 on 2007-08-20
Ah, I tried out Seahorse but the only problem is...I run XFCE so it can't show up since it's made for Nautilus.  Isn't there just some sort of archiving sytem I can use?  Like winrar but...not winrar?  Haha, thank you for your help so far though!

---

### Post by yopnono on 2007-08-20
> **donut2790 said:**
> Ah, I tried out Seahorse but the only problem is...I run XFCE so it can't show up since it's made for Nautilus.  Isn't there just some sort of archiving sytem I can use?  Like winrar but...not winrar?  Haha, thank you for your help so far though!

Test something like Cryptkeepr or [http://ubuntuforums.org/showthread.php?p=3220696](http://ubuntuforums.org/showthread.php?p=3220696)

---

### Post by donut2790 on 2007-08-20
Thank you very much guys!  Got it workin'!

---

