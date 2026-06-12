---
title: "Partitioned Ubuntu and Windows 7... can't Boot!"
date: 2014-09-29
forum: General Help
---

### Post by robin24 on 2014-09-29
[B][SIZE=2][FONT=arial]I am very new to this and hoping someone can offer me advice.

I have an Asus, 64-bit (Windows 7) and partitoned ~20G to Ubuntu 14.04. Now when I start the computor I am taken to the grub rescue screen. This happens when I try to boot either of the devices.
[/FONT][/SIZE][/B]

[B][SIZE=2][FONT=arial]Right now I am using LiveCD to run Ubuntu. I checked Gparted, and my partitions are there as expected. I downloaded and tried Boot-Repair, followed the instructions for recommended repair, but it didnt work. I have the error report and I'm hoping somone can take a look and point me in the right direction. Any help would be appreciated. Right now it is more important to me to be able to boot to Windows

[ [SIZE=4]http://paste.ubuntu.com/8451270/[/SIZE]]("http://paste.ubuntu.com/8451270/")[/FONT]
[/SIZE][/B]

[SIZE=2]**[FONT=arial]Thank you[/FONT]**[/SIZE][SIZE=2]**[FONT=arial][IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG][/FONT]**






[/SIZE]

---

### Post by oldfred on 2014-09-29
Report does not show any grub.cfg nor any kernels?
Did install complete?

It might be easier just to reinstall, but only use Something Else so you can reuse existing / (root) partition. There is a major bug perhaps only with newer UEFI systems where auto reinstalls say they overwrite just Ubuntu but erase entire drive. Best to have full backups and only use something else.

We also normally use ext4 for format not ext3 and have a swap partition, but your install should have worked if it completed and had kernels & grub.cfg or menu.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

