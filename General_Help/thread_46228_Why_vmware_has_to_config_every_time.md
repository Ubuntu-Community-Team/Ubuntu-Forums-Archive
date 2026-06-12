---
title: "Why vmware has to config every time?"
date: 2005-07-03
forum: General Help
---

### Post by jasonhh on 2005-07-03
I am using vmware-gsx-3.1, but every time i reboot my computer(ubuntu 5.04), i have to run the vmware-config.pl, or the vmware can not work, it has to be recomplied every time, could anyone tell me why this happens? Thanks a lot. :)

---

### Post by intangible on 2005-07-04
udev is what cause the problem, vmware hasn't been updated to work with it yet.  There is a fix out there called "vmware any any update".  Here's a link to one: [http://ftp.cvut.cz/vmware/vmware-any-any-update92.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update92.tar.gz)  but you can look around for a more updated one if you need to.

---

### Post by jasonhh on 2005-07-04
Thanks! :)

---

