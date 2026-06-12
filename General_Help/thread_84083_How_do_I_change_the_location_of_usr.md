---
title: "How do I change the location of /usr"
date: 2005-10-30
forum: General Help
---

### Post by yamix on 2005-10-30
When installing ubuntu, I put my /usr partition on a different hard drive.  The problem is, I want to be able to boot without that hard drive in, so thus i want to move /usr to /      (I guess, I'm new to all of this, lol)

How would I go about doing this?

---

### Post by SickTwist on 2005-10-30
Do this with the second hard drive in:
```

sudo mkdir /usr-new
cd /usr
cp -a . /usr-new
sudo umount /usr
sudo mv /usr-new /usr
sudo gedit /etc/fstab

```
Now, find the line in fstab that has /usr in the second column. Comment out this line (put a # at the beginning of it). Then save and close the file. Now you can remove the second drive.

---

