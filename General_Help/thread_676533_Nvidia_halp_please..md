---
title: "Nvidia halp please."
date: 2008-01-23
forum: General Help
---

### Post by zuknivek on 2008-01-23
I have a 7600gt in my home made computer and I cannot install the driver for this thing to save my life. I've tried everything. Envy, automatix, restricted driver install thing, and other methods that i found on this forum. I cant get one of them to work. It would be greatly appreciated if someone could tell me which driver i need to download and how to install it manually with terminal.

---

### Post by pointone on 2008-01-23
The driver available through the restricted drivers manager should be sufficient. What happened when you tried to use this?

---

### Post by zuknivek on 2008-01-24
when i tried using restricted drivers i received an error about Linux restricted module. From there i went into synopsis upgrade under administrative (not sure on names) and then installed the thing needed for Linux module restricted drivers and it said restricted drivers were not needed for my video card. If it isn't my video card then it is probably that i'm running linux inside of windows with virtual box. Maybe i did something wrong with virtual box that made me not able to install video drivers for ubuntu.

---

### Post by pointone on 2008-01-24
VirtualBox uses special custom drivers; you are not required nor able to install drivers yourself. This has to do with the way VirtualBox allows the virtual machine to access your physical hardware. Install the VirtualBox Guest Additions for better video support, but it is not possible to get 3D acceleration in VirtualBox at this time. Try taking a look at Xen if you require this.

---

### Post by zuknivek on 2008-01-24
Thank you very very much. I am very relieved that it wasn't just my abilities to install a driver on ubuntu. Thank you again very much.

---

