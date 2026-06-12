---
title: "Only Superuser can mount?!?"
date: 2006-10-27
forum: General Help
---

### Post by Prospero2006 on 2006-10-27
I have a room full of student ubuntu machines. All of the students have
pen drives, but right now they can't mount them because of this:

mount: only superuser can mount.

I don't want to hand out the root password.

Any suggestions on how I can get regular users to mount these block devices?

Thanks, 
Pros

---

### Post by johann_p on 2006-10-27
> **Prospero2006 said:**
> I have a room full of student ubuntu machines. All of the students have
pen drives, but right now they can't mount them because of this:

mount: only superuser can mount.

I don't want to hand out the root password.

Any suggestions on how I can get regular users to mount these block devices?

Thanks, 
Pros

This sounds extremely serious. Can anyone confirm this?

---

### Post by beerorkid on 2006-10-27
cant they just sudo mount .......?

---

### Post by christhemonkey on 2006-10-27
No because then they need the administrator password?


I would suggest using pmount
```
pmount device [ label ] 
```

From the man page:
> pmount  ("policy mount") is a wrapper around the standard mount program which permits normal users to mount removable devices without a  matching /etc/fstab entry.


EDIT: Just remembered, all the users must be in the **plugdev** group.
To add them do this:
```
sudo adduser user plugdev 
```

---

### Post by bmillsap on 2006-10-27
Disclaimer: speaking from limited experience here, since I'm currently learning this stuff myself.

The man page for mount gives an example of an fstab line that would allow a user to mount a cd-rom filesystem without needing to be root (very similar situation).  Could that be adapted to this situation by having a similar line in fstab that just changed the device to be the usb port?

---

### Post by foolishchild on 2006-10-27
Or automount? using autofs.

---

### Post by Tambo on 2006-10-27
You will need to edit /etc/fstab and add a line corresponding to the device in question, probably /dev/sda1. You will need to set it to umask=000. Or you could put them all in a group and put gid=<groupid> in the line.

---

