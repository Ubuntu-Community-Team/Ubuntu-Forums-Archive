---
title: "help!!!"
date: 2008-05-05
forum: General Help
---

### Post by shashwat0805 on 2008-05-05
i have a windows xp service pack 2 so all i need to lnow is hat can i have ubuntu and xp both simultaneously on my system.
or is there any way of keeping both of them on the system:)

---

### Post by bryncoles on 2008-05-05
hi shashwat0805. 

I also have windows XP on my system (a packard bell easynote r series). It has no problems playing alongside ubuntu (7:10 upgraded to 8:4). so assuming my experience is typical, you should be able to set up as a dual boot system without any problems. 

when installing from the live cd (thats the install cd with ubuntu on it), make sure you select the 'guided partition' install option, and allocate about half of your hard drive to ubuntu.

oh - and make sure you have defragged windows before you install! otherwise you might risk compromising some of your data. 

when you turn your computer on, it will ask you which operating system you want to boot - with ubuntu as the first option on the list and windows xp as the last.

*edit*

this guide might help you...

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Dyqik on 2008-05-05
Hi,

I have several machines with both Ubuntu and XP on the same hard disk, in different partitions.  After following the standard install instructions, the only issue in making them play nice together is that you have to fully shutdown XP to be able to read and write hard disks in Ubuntu that you use in XP (and vice versa).  There's no real way around this as it's inherent to the way disks work in all operating systems

You can read Ubuntu disk partitions in Windows XP by installing the Ext2fsd 
driver.

Good luck with Ubuntu!

---

### Post by Locke_99GS on 2008-05-05
Hardy kept bothering me about having to go to windows and "safely remove hardware" or "eject" my NTFS disc before it would mount it - even with proper shutdowns in XP. I had to mount the NTFS disc in terminal with *force*, and then unmount it, afterwhich it would mount with *default* in terminal. (to test) I then added it to fstab with *default* and it works properly.

---

