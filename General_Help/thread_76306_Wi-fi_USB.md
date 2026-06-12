---
title: "Wi-fi USB"
date: 2005-10-14
forum: General Help
---

### Post by julio on 2005-10-14
Is there any way to connect a Wi-fi USB device to Ubuntu? I'm connnected with it on my Windows partition, but I don't know any way to get it working on Ubuntu. Any help would be great. Thanks in advance.

---

### Post by az on 2005-10-15
You will have to specify which device you have (the chipset)

Plug it in and look in the device manager to see how it is recognised.


Most of them should work fine.  Just go to networking and set up your connection.

If you have a device that needs a special driver, use ndiswrapper.
[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

I know that my dwl-122 needs some funny stuff to work (I could use ndiswrapper, but I prefer to use thelinux driver)
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-September/010439.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-September/010439.html)

---

### Post by kiddyfurby on 2005-10-15
check out the zd1201 driver
I think you will need to download the firmware into place for the driver to work

---

