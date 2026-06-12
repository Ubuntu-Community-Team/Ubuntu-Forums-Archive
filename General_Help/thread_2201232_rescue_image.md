---
title: "rescue image"
date: 2014-01-23
forum: General Help
---

### Post by russellhearn691 on 2014-01-23
as the title says i'm looking to make a rescue image of my current ubuntu server install, all i would like to do is have bookable media whether it be a dvd or a usb so if anything happens to my system i can plug it in and restore my server to what it was before it went sideways, i would prefer to have a backup without the free space but i do need all the data saving as i have a website on it and a seedbox.
 
If at all possible, please lend a new user a helping hand

Thanks

---

### Post by Bucky Ball on 2014-01-23
You could try Remastersys. It will make an ISO of your install which you can burn to install media. ;)

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

It is not maintained anymore (all though this seems to be an 'on again off again' thing) but works great. There is also a front-end GUI for it if you prefer not to work in the terminal. 

Clonezilla is another possibility, but I think that copies free space, too (clones the partition exactly as is). There is a way to create an ISO from a Clonezilla image also. You need to boot Clonezilla from its own install media rather than on a running install.

Clonezilla is in the repos.

---

### Post by zteam2 on 2014-01-23
> **Bucky Ball said:**
> You could try Remastersys. It will make an ISO of your install which you can burn to install media. ;)

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

It is not maintained anymore (all though this seems to be an 'on again off again' thing) but works great. There is also a front-end GUI for it if you prefer not to work in the terminal. 

Clonezilla is another possibility, but I think that copies free space, too (clones the partition exactly as is). There is a way to create an ISO from a Clonezilla image also. You need to boot Clonezilla from its own install media rather than on a running install.

Clonezilla is in the repos.

No, Clonezilla doesn't clone the free space, not if you just stick with the default settings.
It actually Cloned my whole system in about 6 minutes (but that was to harddrive of course)

---

