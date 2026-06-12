---
title: "Mount's dissapear on re-boot, then act strangely"
date: 2007-12-20
forum: General Help
---

### Post by tuproxy on 2007-12-20
I am running 7.10 Desktop

I have 5 SATA drives that are NTFS. I didn't think they could be R/W without a module, but I guess that is an upgrade in 7.10 from 6.10? These drives were installed on a 6.10 system, I re-installed 7.10 after formatting the OS HD. Now these drives are coming up in the "Computer" places menu, but I have to enter a password to access them for the first time. Why is this?  Also I thought I had to edit my fstab to get these drives to show up or is that a new addition?

When I remotely reboot via SSH and then login, these drives are not listed in my /media/ folder.  If I login to the desktop and then click on the drive, enter the password, they show up via SSH. Why is this? How can I access them without having to go to the desktop and click on the first?  Is this a mount issue?  can this be changed with my fstab?

---

### Post by ~LoKe on 2007-12-20
Probably some sort of autodetect.  It would need a password to mount them to /media.  I imagine if you write them into your fstab the password should no longer be required.

---

### Post by tuproxy on 2007-12-20
That makes sense. 

Is there a way to rename the disks? They are being mounted to the same spot where my last install mounted them, which is strange I think. I don't know how they got the same titles/names too.

BTW, what is the command to see the remaining disk space?

---

### Post by ~LoKe on 2007-12-20
> **tuproxy said:**
> That makes sense. 

Is there a way to rename the disks?
You can do so when you specify a mount point in /etc/fstab.

> **tuproxy said:**
> 
BTW, what is the command to see the remaining disk space?

```
df
```

---

