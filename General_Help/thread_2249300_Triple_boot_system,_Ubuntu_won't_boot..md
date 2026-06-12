---
title: "Triple boot system, Ubuntu won't boot."
date: 2014-10-21
forum: General Help
---

### Post by Jason Spaceman on 2014-10-21
I have a triple boot system (Win7, Ubuntu 14.04, and OS X Yosemite).  I'm using the Clover bootloader to select which OS to boot.  After upgrading to Yosemite (or perhaps it was due to upgrading Clover), Ubuntu no longer boots.  I just get a black screen with a flashing cursor.  In the past I would select Ubuntu from the Clover menu, Clover would hand things over to Grub, and Grub would load Ubuntu.  Grub was on the Ubuntu partition (/dev/sda6) and not on the MBR.  

Do I need to reinstall Grub?  Is there a way to do it without the Live CD, as I can't seem to find mine at the moment?

---

### Post by yancek on 2014-10-21
[FONT=comic sans ms]Have you read the documentation at their web site?  

[http://clover-wiki.zetam.org/Home](http://clover-wiki.zetam.org/Home)
[/FONT]

---

