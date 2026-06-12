---
title: "ACPI PCC probe failure and COMRESET"
date: 2015-08-26
forum: General Help
---

### Post by Dr.Leet on 2015-08-26
I have an Asus UX32VD running Xubuntu 15.04 64bit. When I start the PC it says ACPI PCC probe failed and COMRESET failed. See the picture in the bottom for the whole error message.
It have tried running Ubuntu, Arch Linux and Linux Mint and they all produce the same error message. I tried physically removing my hard drive and booting from a USB and the error ocurred once again. I have already verified that UUID's in fstab and GRUB match, so that is not the problem.
I am not sure what kind of output to post, in order for you to help so please let me know.
Any ideas?
Thx in advance.
[IMG]http://i.imgur.com/QrkvUf0.jpg[/IMG]

---

### Post by grahammechanical on 2015-08-26
The message "ACPI probe failed" started appearing during the 26 week development period of Ubuntu 15.04. It never stopped my system from loading.

It was also during the 15.04 development period that Ubuntu switched from using Upstart as the init system to using SystemD. "Starting version 219" is a referece to the SystemD version being loaded.

It is the "COMReset failed" message that points to the real problem.

[http://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error](http://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error)

[http://www.linuxquestions.org/questions/debian-26/new-gpt-drive-and-comrest%3D16-4175550911/](http://www.linuxquestions.org/questions/debian-26/new-gpt-drive-and-comrest%3D16-4175550911/)

There seem to be different opinions on what is causing this.

Regards.

---

### Post by Dr.Leet on 2015-08-26
Could it be related to the iSSD (Hybrid SSD) on the motherboard? I don't think there is anything else connected to a SATA port other than my hard drive except maybe the iSSD.

---

