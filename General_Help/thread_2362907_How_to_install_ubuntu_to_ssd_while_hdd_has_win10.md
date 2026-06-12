---
title: "How to install ubuntu to ssd while hdd has win10?"
date: 2017-06-03
forum: General Help
---

### Post by dunya on 2017-06-03
I installed Win10 on 1tb hdd and now want to install ubuntu 17.04 to 128 gb hdd, but have no idea how to do it. Is there any document that can guide me, or someone be kind enough to write here the steps?

---

### Post by yancek on 2017-06-03
Start by reading the Ubuntu documentation at their site at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-06-03
Did you install Windows 10 in UEFI or BIOS boot mode?
How you boot install media UEFI or BIOS is then how it installs, same with Ubuntu.

And you want both systems installed in same boot mode.
But if newer hardware with UEFI, probably better to use UEFI, not the 35 year old but well known BIOS/MBR configuration.
See link in my signature below.

If easy to unplug HDD, then easy to just install to SSD. 
If not easy to unplug be sure to use Something Else install option. Often easier to create partitions in advance, but still have to choose which partition you want for / (root) and which for /home if you want that separate.

       MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

If installing in BIOS mode, you need to install grub2's boot loader into SSD as you want to keep Windows boot loader in Windows drive.
If UEFI grub only installs to drive seen as sda, and will automatically put its files into the ESP - efi system partition. 

 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

 Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

