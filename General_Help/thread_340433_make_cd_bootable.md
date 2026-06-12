---
title: "make cd bootable?"
date: 2007-01-17
forum: General Help
---

### Post by johnarild on 2007-01-17
I have an old win98 cd I want to use in a VMware session, but the cd is damaged and I can't make an ISO out of it, but I can copy all the files that I need for an installation. 
  My question is, how do I extract the boot sector from the cd and put it in an iso that I'll make with mkisofs?
  From what I understand I can use the following command to make the iso bootable.
```
mkisofs -r -b boot.img -c boot.catalog -o win98.iso ./ 
```
  But I need to extract the boot.img from my Win98 cd first. 

Thanks,

---

