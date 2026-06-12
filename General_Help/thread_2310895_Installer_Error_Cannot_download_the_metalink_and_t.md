---
title: "Installer Error: Cannot download the metalink and therefore the ISO"
date: 2016-01-22
forum: General Help
---

### Post by delquesto on 2016-01-22
Greetings,


I'm new to the Linux world and want to install Ubuntu 14.04.3. 

I wanted to set it up as a dual system with my Windows 8.1 x64

After creating a UEFI bootable flash drive with the extracted ISO, I run the setup (wubi.exe).

My hard drive has a ready partition with sufficient space for installation, but after the initial setup window (which drive to install to, username, password etc.) I get the following message during installation:

**"Cannot download the metalink and therefore the ISO" :**

[IMG]http://i66.tinypic.com/517q0j.png[/IMG]

I am connected to the internet. What can be the problem?

All help greatly appreciated :)


Many thanks,
del~

---

### Post by hakuna_matata on 2016-01-22
> **delquesto said:**
> 
After creating a UEFI bootable flash drive with the extracted ISO, I run the setup (wubi.exe).

> **delquesto said:**
> 
What can be the problem?

If you have a bootable flash drive with the ISO, just boot from it and don't run wubi.exe. If your flash drive is still not bootable, try [Rufus]("https://rufus.akeo.ie/") to put the ISO to the flash drive.

---

### Post by grahammechanical on 2016-01-22
One more thing.

Do not use wubi.exe. It is incompatible with Windows 8.1 and later Windows versions. It is no longer being developed and in the past few forum users had any experience with Wubi installations. And that situation has not changed. So, do not expect much support with a wubi.exe install.

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

It is best to do a proper dual boot with Ubuntu. If you choose to do that then I suggest that it would be better to upgrade to Windows 10 before installing Ubuntu. Many have upgraded to Windows 10 after installing Ubuntu and have hit problems.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards

---

### Post by delquesto on 2016-01-23
Thanks for your help guys,

Rufus solved the issue for me and all is working fine now.

I didn't want to upgrade to Win 10 - in fact the main reason I am switching to Linux is because I hate IOS and disagree with Win 10 privacy policies.


Cheers for the help!
del~

---

