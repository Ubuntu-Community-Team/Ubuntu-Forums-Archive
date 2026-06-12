---
title: "Dual boot: Ubuntu and kali linux"
date: 2014-11-30
forum: General Help
---

### Post by hezy2 on 2014-11-30
Hello,
I may need to install the mentioned vers. of linux on one leptop, on single HD. There's already Kali linux installed on it. I want to ask if there's something I should consider before intalling ubuntu and for good reason to prevent GRUB problems. Thanks,
hezy.

---

### Post by oldfred on 2014-11-30
Only use Something Else, and manually set up partitions. I prefer to create partitions in advance with gparted, but that is only slightly easier and you still have to use Something Else. With one drive you do want combo box to say drive that is sda, not partition like sda1 etc.

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

---

