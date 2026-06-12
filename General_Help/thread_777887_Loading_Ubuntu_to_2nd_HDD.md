---
title: "Loading Ubuntu to 2nd HDD"
date: 2008-05-01
forum: General Help
---

### Post by Beetlebum on 2008-05-01
Complex one to start the ball rolling.............. 

Here we go....... I want to install Ubuntu to a 2nd HDD. On the IDE HDD 0 I have Windows 2K and XP. I want to install Ubuntu to the 2nd  HDD, an SATA drive. I also use Bootit as my boot manager.  

Problem. Ubuntu installs fine to the 2nd HDD, if I remove the IDE from the equation. However, if I re-attach the IDE drive, Ubuntu overrides the boot manager and I cannot boot Windows. I can use a floppy boot manager but that's hardly ideal. 

What I need is a way to install to the 2nd HDD without messing with Windows, and keeping the boot manager intact. 

Shame, as from early impressions Ubuntu looks very good indeed!

---

### Post by chewearn on 2008-05-02
Never heard of Bootit; is this what you are referring to:
[http://www.terabyteunlimited.com/index.htm](http://www.terabyteunlimited.com/index.htm)

A straight forward thing to do is:
1. remove the IDE
2. install ubuntu on the SATA
3. you plug the IDE back in

Now, you can test boot each harddisk.  Use the BIOS to select the IDE as primary boot device.  This should get you to Bootit and to Windows.

Then, change the BIOS to SATA as primary boot device.  This should get you to Grub and Ubuntu.

If the above scenario works, you should be able to go into Bootit bootloader configuration, add a new entry for Ubuntu.  As mentioned above, I'm not familiar with this apps, so not sure if this is possible.

Alternatively, you can add the Windows part to Grub menu.  Discounting any complication that might be added by Bootit, the usual way to add Windows into Grub menu is explained in the part titled: "Only read below if Windows is now missing from the boot menu"
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot")

.
[ ]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot")

---

