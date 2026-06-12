---
title: "formating the entire HD"
date: 2005-08-14
forum: General Help
---

### Post by kobix on 2005-08-14
Hi

I was trying to insall ubuntu but this caused many problems. I need to format my entire HD now. Is there is a way to do this from the live version?

Thanks, Koby

---

### Post by nad on 2005-08-14
Formatting a hard drive is the process of setting up a filesystem. If this is what you wish to do, there are several tools on the live cd to do so.

My question to you is why do you wish to create a file system when you apparently need to install an operating system? What were the "problems" caused by the ubuntu install?

---

### Post by kobix on 2005-08-14
Yes. It damaged the MBR. I even tried to install windows from scratch but could not.

Thanks.

---

### Post by nad on 2005-08-14
Well... I wouldn't call it "damaged", but ubuntu probably wrote to the mbr in order to setup your requested dual boot system. There are methods to boot to a linux system without a boot loader in the mbr.

If you wish to reinstall Windoze and your install disk is giving you a fit, try a win98 boot disk and the fdisk utility with the \mbr switch. If I recall correctly, there is also a utility called fixmbr.exe(com).

As the mbr is before any filesystem on your disk, you will need a utility such as these to accomplish what you wish.

---

