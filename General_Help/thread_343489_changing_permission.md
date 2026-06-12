---
title: "changing permission"
date: 2007-01-21
forum: General Help
---

### Post by SVWander on 2007-01-21
I had to reintall Windows XP on my dual booting system before I did I copied Documents and Setting to Ubuntu. I would like now to be able to copy these files onto my XP's hard drive but here I am stumped by permissions. Right now these files are in /media/documents and I would like to copy them to /media/windows . . . anywhere would be find. My eyes are going blurry trying to figure out how to do this. Can anyone help me figure out the command lines needed to transfer these files?

Thank you, Tim

---

### Post by taurus on 2007-01-21
Applications -> Accessories -> Terminal
```
sudo cp /media/documents/* /media/windows
```

---

### Post by SVWander on 2007-01-22
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo cp /media/documents/* /media/windows
```

desktop:~$ sudo cp /media/documents/* /media/windows
cp: omitting directory `/media/documents/doc'

I thought it might not be copying because of the directories set up below documents/ but that is not it. It is still not copying.  tm

---

### Post by taurus on 2007-01-22
```
sudo cp -R /media/documents/* /media/windows
```

---

### Post by SVWander on 2007-01-22
> **taurus said:**
> ```
sudo cp -R /media/documents/* /media/windows
```

still no cigar:

-desktop:/media$ sudo cp -R /media/documents/* /media/windows
cp: cannot create directory `/media/windows/doc': Read-only file system

I feel like I am butting my head against a brick wall. LOL but it is fun. tm

---

### Post by taurus on 2007-01-22
If you want to write to your XP (ntfs), you need to install ntfs-3g first.  

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Otherwise, install fs-driver so you can read ext2/ext3 from XP.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by SVWander on 2007-01-22
Thank you so much for your help! I am learning a little bit everyday. tm

---

