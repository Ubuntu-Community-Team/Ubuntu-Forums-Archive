---
title: "ubuntu 11.1 I am not able to access admin"
date: 2013-08-20
forum: General Help
---

### Post by john_ling on 2013-08-20
When ubuntu installed the password for admin was already set.
Also how do i install drivers for the wifi. I have the disc with the windows drivers.

---

### Post by dragin-mm on 2013-08-20
Try - sudo passwd su - to change admin password.

---

### Post by deadflowr on 2013-08-20
11.10?
If this is the version you're running, then trying to install anything, regardless of whether you have admin rights or not, will be for naught.
That release is dead, as of April, and the repositories were moved.

You would be best to Upgrade to a supported release.

And as far as admin rights, if you can sudo without errors or permission denied, then you have admin rights.
So no need to change or make root password.
If you need to run as root for a prolong period, I suggest using
```
sudo -i
```
Which will switch the user into interactive sudo/root.
To close the sudo -i root session, simply type exit and then hit enter.

---

