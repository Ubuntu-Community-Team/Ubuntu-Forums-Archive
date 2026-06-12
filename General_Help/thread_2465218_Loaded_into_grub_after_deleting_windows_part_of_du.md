---
title: "Loaded into grub after deleting windows part of duel boot"
date: 2021-07-25
forum: General Help
---

### Post by bruhmomentlmao on 2021-07-25
So I uninstalled my windows section of my duel boot and after I restarted I was met with the gnu grub2 screen. I’m not really sure how to get back into Ubuntu from grub and set it to auto load into Ubuntu once I power on my system

---

### Post by oldfred on 2021-07-25
If Ubuntu was default boot, then removing Windows should not have changed booting.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2021-07-26
When we dual boot it is the Grub boot menu that gives us the options as to which OS to load. Perhaps you are getting the Grub rescue prompt? And not the Grub menu. That would indicate that Grub cannot find its configuration file (grub.cfg). It cannot draw a Grub menu for you with an option to load Ubuntu or Windows.
 
How, exactly, did you uninstall the Windows part of the dual boot? 

Regards

---

### Post by bruhmomentlmao on 2021-07-26
I used a tool in Linux to delete it but i forgot what it’s called but I might just reinstall Ubuntu because I think that will work

---

### Post by yancek on 2021-07-26
Which version of windows did you have installed?
Was it an EFI install?  Which partitions did you delete?  System and EFI?
Can you boot Ubuntu from the Boot Options in the BIOS firmware?
It would be helpful if you remembered the Linux tool you used as generally in this situation from Linux, one would simply format the windows system partition

---

