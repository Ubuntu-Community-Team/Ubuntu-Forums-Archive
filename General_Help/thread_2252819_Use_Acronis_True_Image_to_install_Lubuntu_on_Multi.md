---
title: "Use Acronis True Image to install Lubuntu on Multiple Computers"
date: 2014-11-14
forum: General Help
---

### Post by West Swan on 2014-11-14
Hello,

I install Lubuntu 14.04 on quite a few old computers.

Can I install it on one computer, get everything how I want it (including all updates, uninstalling some programs, installing some others and finally creating an image) that can be used to more quickly install Lubuntu on other computers?

One thing I wouldn't do is 'install additional drivers'

I have used Acronis many times in the past and would prefer using it to any other method - unless the other method was easy and could be done without having to use the terminal.

Regards,

Paul

---

### Post by West Swan on 2014-12-03
Bump - I waited two weeks please don't get angry :p

---

### Post by rbmorse on 2014-12-03
I suspect it would be OK as long as the machines weren't put on the same local network. They'd all have the same machine names and UUID's, etc.

---

### Post by Bucky Ball on 2014-12-03
You could create an ISO using Clonezilla, but you may get the same issue as outlined above. See here:

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Don't know anything about Acronis, sorry. Good luck.

---

### Post by ian-weisser on 2014-12-03
There are three install options that are native Ubuntu, fully supported, and avoid the duplicate-UUID problem, plus a couple variations for your customizations:

1) Walk around and use a normal physical install media for each entire install. Uses the network only for updates.
You can customize the physical install media with a preseed file, or you can use the OEM installer, or your can manually customize after installation is complete.

The preseed file is a great way to add/remove software without remastering the install image.
See [https://help.ubuntu.com/10.04/installation-guide/i386/preseed-using.html](https://help.ubuntu.com/10.04/installation-guide/i386/preseed-using.html)

The OEM installer is very useful if you don't want to set up all the user accounts, locale settings, etc. during the install - the user will create an account and choose locale during their first boot. You can also add/remove software.
See [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)


2) Walk around and use a physical media to install a bootable, networkable minimal system. Installing ubuntu-minimal is very fast, so you don't need a lot of physical media. Your custom script can then install the rest of the system over the network.
See [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


3) Netboot the systems into a server-based install image. No physical install media may be needed at all. If that install image has a preseed file or OEM installer, even better.
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)


Personally, If I were installing on 3 computers at once, I would use #2. 
If I were installing on 300 computers simultaneously, I would set up a server and use #3.

---

