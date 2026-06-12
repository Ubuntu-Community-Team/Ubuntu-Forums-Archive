---
title: "Wubi Wipeout old system"
date: 2008-05-01
forum: General Help
---

### Post by madtom1999 on 2008-05-01
I have a few machines without bootable CDRoms that I would like to convert to the Ubuntu family.
I've not been able to make a usable boot floppy from about 50 media!
Can I use Wubi to take control of the machine and then do a standard install from the CD? 
Also can I do similar for a network install?

---

### Post by msjones on 2008-05-01
Hi, I dont this is possible with wubi.

It acts only like a virtual machine, or bootcamp for OS X. Have you got a computer already installed with ubuntu? You could setup these machines to install from a network source as aposed to the bootable media.

How old are these machines?

---

### Post by avtolle on 2008-05-01
Simply, Wubi installs as a Windows .exe file, downloads Ubuntu, puts it in a folder, and creates a Grub like menu to give one the choice of booting into Windows/Ubuntu. I've used it to install 8.04 on a Vista laptop without issues. Depending upon how old the computers are, and the RAM, etc., it may work for you. It is not a "virtual machine"; when one boots into Ubuntu, one is running Linux. HTH.
See this for additional information, together with links to the official web page and guide:
[http://ubuntuforums.org/showthread.php?t=777323](http://ubuntuforums.org/showthread.php?t=777323)

---

