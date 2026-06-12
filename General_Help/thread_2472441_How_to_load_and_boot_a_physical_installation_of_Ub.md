---
title: "How to load and boot a physical installation of Ubuntu inside the RAM memory and how"
date: 2022-02-27
forum: General Help
---

### Post by marietto2008 on 2022-02-27
Hello.

Is there a method to load and boot a physical installation of Ubuntu inside the RAM memory of the PC ? I've already installed Ubuntu with a lot of programs installed inside,I don't need to do this. I need to understand how to run everything from the memory. And I also need to understand how to write the changes I do to the OS permanently on a SATA disk. I'm using ubuntu 21.10. very thanks.

---

### Post by him610 on 2022-02-27
I have never done what you are attempting to accomplish; however, you may want to review this webpage, [https://linuxhint.com/ramdisk_ubuntu_1804/]("https://linuxhint.com/ramdisk_ubuntu_1804/") 
The information presented there probably still holds true for later releases, ie 21.10.

---

### Post by MAFoElffen on 2022-02-27
Well... You do a ramdisk load every time you boot Ubuntu Linux. initramfs initially loads to a ramdisk during the boot...

I very much liked that article that him610 posted. Thank you for that.

And a LiveCD and a PXE booted image for a thin client both do those, right? The filesystems of both are not persistent and only reside in volatile memory. 

What are you trying to do and what is your goal?

---

