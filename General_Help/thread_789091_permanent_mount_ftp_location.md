---
title: "permanent mount ftp location"
date: 2008-05-10
forum: General Help
---

### Post by feest on 2008-05-10
In previouses releases of ubuntu, a ftp location was permanently mounten untill umounted. In Hardy it's tempoary mounten untill next start. Since I use my ftp connection as an external drive I want to mount it permanently. How do I do this?

---

### Post by x1a4 on 2008-05-10
Hi,

Install FUSE and the cURLFTP file system.

Add FUSE to the kernel (as root)
```
modprobe fuse
```


Add the following to your /etc/fstab
```
curlftpfs#user:password@ftp.host.net /mount/point fuse user,disable_eprt,noauto
```

Mount it
```
mount /mount/point
```

---

### Post by feest on 2008-05-10
I've done this but I can't acces my server since it says that i don't have permissions to see it. I was unable to chmod it to 777 but using sudo nautilus i've made some changes to it.

Now when I click on the icon i got the message that there is no application suitable for the filtype specified. 

Isn't there an easy way to do this? Why is this functionallity removed with hardy?

---

### Post by feest on 2008-05-12
anyone?

---

### Post by Mr K on 2008-06-03
Insert fuse options at the end of the line:```
-o umask=777,uid=1000,allow_other 
```
Hope this helps!:)

---

