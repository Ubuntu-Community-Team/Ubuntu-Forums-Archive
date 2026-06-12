---
title: "Need help installing in VIRTUAL BOX"
date: 2013-01-13
forum: General Help
---

### Post by rittik on 2013-01-13
Hey so am facing some problems using it in vb.
i downloaded 12.04 from ur website downloads
 its in .iso file..when i try to import it in vb it shows this error
[IMG]http://i1192.photobucket.com/albums/aa325/Rittikbhowmik/untitledsefsgefgs_zpsa9b74e01.png[/IMG]

what to do?
i dont want to multiboot my pc by installing wubi

---

### Post by 2F4U on 2013-01-13
What exactly do you mean by "import"? Usually, you create a new virtual machine, then VB asks you for the install image and you go on to install Ubuntu in a virtual machine.
Did you verify that the checksum of the downloaded iso file matches?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by drpjkurian on 2013-01-13
what you have inserted in the cd drive for installation of Ubuntu appears to be an .iso file. This format (.iso) is an image file of the OS, therefore I request you to burn the image file to a CD

---

### Post by 2F4U on 2013-01-13
> **drpjkurian said:**
> what you have inserted in the cd drive for installation of Ubuntu appears to be an .iso file. This format (.iso) is an image file of the OS, therefore I request you to burn the image file to a CD

No, there is no need to burn the iso onto a CD. From the VirtualBox manual:

[https://www.virtualbox.org/manual/ch01.html#gui-createvm](https://www.virtualbox.org/manual/ch01.html#gui-createvm)

> If you have downloaded installation media from the Internet in           the form of an ISO image file (most probably in the case of a Linux           distribution), you would normally burn this file to an empty CD or           DVD and proceed as just described. With VirtualBox however, you can           skip this step and mount the ISO file directly. VirtualBox will then           present this file as a CD or DVD-ROM drive to the virtual machine,           much like it does with virtual hard disk images.

---

### Post by rittik on 2013-01-13
I am on Widows XP SP3 and Yes i selected .iso after creating a virtualachine ten going to its settings>storage and then selecting .iso
After clicking on the .iso to select it gives that error..and what donu mean by checksum? would like to do it..i followed your link but got a bit confused there

---

