---
title: "How do i find out the uuid of a partiton on a usb drive"
date: 2008-06-22
forum: General Help
---

### Post by markp1989 on 2008-06-22
im looking to set up a custom install on a usb drive, that has the main root partition  in squashfs, and then writes changes to the second partition using unionfs  


i have all the files i want to add to the squashfs, i just need to know how to find out the uuid of the second partiton on the usb drive,

how do i find this out?

Thanks Markp1989

---

### Post by sisco311 on 2008-06-22
```
sudo blkid
```

---

