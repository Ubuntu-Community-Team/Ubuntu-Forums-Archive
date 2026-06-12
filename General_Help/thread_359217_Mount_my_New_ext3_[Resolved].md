---
title: "Mount my New ext3 [Resolved]"
date: 2007-02-11
forum: General Help
---

### Post by gabbman on 2007-02-11
I took the spare NTFS drive on my Vaio laptop, and reformated it to an ext3 partion.  
I changed my fstab to reflect the changes, however I have to manually mount it when I want to copy files.  What to I have to change in the fstab line to make that happen?

"/dev/hda5       /media/hda5     ext3	user,exec,rw,noauto	0 0"

---

### Post by aysiu on 2007-02-11
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help.

---

### Post by taurus on 2007-02-11
Remove the old line in /etc/fstab and replace that with this one.

```
/dev/hda5   /media/hda5   ext3   defaults   0   1
```
Save it.  Now, change the ownership of /media/hda5 to you so you can write to it.  Assuming your login name is **gabbman** (replace with the right one if it is not), do

```
sudo chown -R **gabbman**:**gabbman** /media/hda5
```
Reboot.

---

### Post by gabbman on 2007-02-11
Thank you.  That was the last remaing evidence of anything microsoft on the laptop, she's free now. :)

---

