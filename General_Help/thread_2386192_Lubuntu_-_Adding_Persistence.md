---
title: "Lubuntu - Adding Persistence"
date: 2018-03-02
forum: General Help
---

### Post by houston39 on 2018-03-02
Friends,

Is there a way to add persistence to a USB drive for Lubuntu?  I really enjoy the speed of the product, I would just like it to retain my wi-fi connection, plug-ins, etc..  If there is a way what is the procedure for adding it?

Thanks!!!!
George

---

### Post by ajgreeny on 2018-03-02
How you do it will depend on the application you use to create the bootable USB; what are you using at present?

---

### Post by sudodus on 2018-03-02
You can create a persistent live system or an installed system (installed like in an internal drive, but in this case in a USB drive). See the following links,

**- Persistent live USB:**

[How to Create Persistent USB Key ...](https://askubuntu.com/questions/975196/how-to-create-persistent-usb-key-with-linux-17-10/1011216#1011216)
[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

**- Installed in USB:**

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by C.S.Cameron on 2018-03-02
Sudodus instructions above are great, however I prefer to make the first partition Fat32 if the drive is under 8GB and NTFS if over 8GB. This will allow the drive to be used for data when plugged into a Windows machine.

In order to do this pre-format the drive FAT32 or NTFS. When you get to partitioning you will need to use "Something else". Reduce the size of the partition and make a second partition ext4 and use as "/". You may take advantage of a separate home partition by making a third partition ext2 or ext4 and use as "/home". The installer will suggest adding swap space which will allow hibernation.  see also [https://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed/227892#227892](https://askubuntu.com/questions/227614/attempt-to-mount-a-filesystem-with-type-ext4-at-failed/227892#227892)

---

