---
title: "Reformat hard drive"
date: 2007-06-10
forum: General Help
---

### Post by Robotman on 2007-06-10
Hi, I have a dual boot Ubuntu/XP system, and I've backed up the data on a spare internal (IDE) hard drive so I can reformat it.  I want to do this from within Ubuntu... I don't want XP to be able to read the drive.  I also want the whole thing reformatted, not partitioned.  How can I go about reformatting it?

---

### Post by taurus on 2007-06-10
You can use gparted to format it to ext3.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install gparted
```
It now should be in System -> Administration.

---

### Post by Robotman on 2007-06-10
Wow, thanks for the quick reply. :)
I have GParted running, and I'm assuming all I need to do is to "Set Disklabel".  That will set it up for MSDOS by default... so I'm guessing I have to change that.  Is DVH the right choice?  Or am I barking up the wrong filetree, so to speak? ;)

---

### Post by Robotman on 2007-06-10
Heh... never mind. :redface: I just figured out I had to unmount the drive first.... then it all became clear.  Thanks for pointing me in the right direction though. :D

---

### Post by Robotman on 2007-06-10
I need help again.  After a reboot, the newly ext3 formatted drive appears in places/computer.... but I need to change the permissions for it so I can write to the drive.  How do I do this?

---

### Post by taurus on 2007-06-10
Where do you mount that ext3 partition?  _Assuming_ you mount it to /media/storage and your login name is **rob**, just change the ownership of /media/storage from root to your login name.

```
sudo chown -R **rob**:**rob** /media/storage
ls -la /media
```

---

### Post by Robotman on 2007-06-10
This has just gone from annoying to bad.  I entered the above code into a terminal window (inserting my name of course) and then got an error message that the drive couldn't be found.   Now after rebooting, the main Ubuntu splash screen won't go away, I can't open any places/folders on my computer and I can't shut down or reboot either.  How can I fix this problem now?

---

### Post by taurus on 2007-06-10
Exactly what command did you run?  Remember, /media/storage is an example so if you didn't mount that partition to /media/storage, then you shouldn't use /media/storage.

---

### Post by Robotman on 2007-06-10
I entered the code exactly as it appears above, with my name instead of rob.  I didn't know /media/storage was just an example... I know nothing about the file system so it looked like the legit command to me.  I have no idea where the drive should be mounted normally.  Is fixing this a relatively simple procedure?

EDIT: my main boot drive was just scanned before rebooting (happened automatically) and now everything appears to be back to normal.  I still don't have write access to my reformatted drive though.

---

### Post by taurus on 2007-06-10
In my previous post, I _assumed_ you mounted it to /media/storage.  Where exactly did you mount it?  Do you mount it from /etc/fstab?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Robotman on 2007-06-10
I found the mount point by mounting it and clicking Properties.  It's mounted to /media/disk.

---

### Post by taurus on 2007-06-10
In that case, do

```
sudo chown -R **rob**:**rob** /media/disk
ls -la /media
```
Again, replace **rob** with your login name.

---

### Post by Robotman on 2007-06-10
That worked. :D I was able to change permissions and now I can use my drive for storage.  Thanks for your help taurus.

---

### Post by taurus on 2007-06-10
No problem, mate.

---

