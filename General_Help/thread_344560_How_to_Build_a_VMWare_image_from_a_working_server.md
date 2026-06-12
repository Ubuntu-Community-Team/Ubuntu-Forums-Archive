---
title: "How to: Build a VMWare image from a working server"
date: 2007-01-23
forum: General Help
---

### Post by salvo1 on 2007-01-23
Hi all,
I've a working ubuntu server (proxy/fax/mail).

I need to build a .vmx file (that is to say a virtual machine file for VMWare) of the whole system.

I tryed to use my "2007-01-11_03.00.04.398249.serverlinux.ful", that is to say the backup folder created with sbackup.
So that, i restore all folders (one by one!) and started my new virtual machine!

The screen stops 1..2 minutes on the first screenshot...
...then i see the other screenshot.

How can i build an exact copy of my system for a virtual machine?

Thanks in advance,
Salvo.

---

### Post by dedmin on 2007-01-23
The new version 6 of VMware Workstation has this , but is still beta. I did this with no hassle. You can make image of the server and then restore it in the virtual machine. First make the vm with size >= of the size of the server, boot with LiveCD and restore the image.

---

