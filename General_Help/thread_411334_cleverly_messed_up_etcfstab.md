---
title: "cleverly messed up etc/fstab"
date: 2007-04-16
forum: General Help
---

### Post by cjwilding on 2007-04-16
I have set my hda1 drive with the parameter -o i think it used to be -oe  or  -rw

I did this by accident as i was messing with another line to get an external usb harddrive setup as it was always read only.

The problem is i cant get back into hda1 to change etc/fstab back to what is was before, because it is now read only.

Can anyone help?.

charlie

---

### Post by pointone on 2007-04-16
Boot using the Live CD and mount the drive read-writable. You can edit fstab this way.

---

### Post by cjwilding on 2007-04-17
booted with a ubuntu live CD however when I try to mount I get the following

> 
ubuntu@ubuntu:/$ mkdir new
ubuntu@ubuntu:/$ sudo mount hda1 new
mount: special device hda1 does not exist



just tried this which worked

> 
ubuntu@ubuntu:/$ mount -o remount,rw /new


---

