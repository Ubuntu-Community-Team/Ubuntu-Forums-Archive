---
title: "resize Ubuntu partion for Windows 8 installation"
date: 2015-08-06
forum: General Help
---

### Post by Alec_Hewitt on 2015-08-06
Hello. I am having trouble re-sizing my partion with GParted to allow me to install Windows 8. I'm trying to create two partions (one for each OS), but Ubuntu is already installed on the hard drive (it's partion takes up the entire 1tb HDD). I have read other threads many times over and tried off swapping. When I click re-size, it wont let me reallocate space. This is probably something extremely rudamentary that I don't understand (i'm new) so thank you! Ive posted a screenshot as well.

Screenshot: [http://imgur.com/xwTrOi2](http://imgur.com/xwTrOi2)

---

### Post by yancek on 2015-08-06
In order to modify partitions, you need to unmount them first.  If you are trying to do this from gparted on the installed Ubuntu, it will fail because the partition is mounted.  GParted is on the Ubuntu Live CD/flash drive so best to use that.  Select the partition you want to shrink (can't really read the image you posted), right click it and select umount and then go ack to the Partition tab and select the resize option.

---

### Post by oldfred on 2015-08-06
Be sure to Boot Windows in UEFI boot mode. It only installs to gpt partitioned drives to boot in UEFI mode. And how you boot installer is then the boot mode it installs.

Once installed make sure you have fast start up off as that is always on hibernation.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by gordintoronto on 2015-08-07
Also, you will need to run Boot Repair after installing Windows.

---

