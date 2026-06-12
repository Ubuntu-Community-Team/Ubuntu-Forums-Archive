---
title: "Uninstalled drivers"
date: 2013-06-28
forum: General Help
---

### Post by CopperShot on 2013-06-28
While installing updates in Ubuntu 12.04, my computer overheated. After rebooting, to my surprise, my mouse wasn't working. Further examination showed that neither were my speakers, wireless networking, ect... (My keyboard luckily still is working. Btw, mousekeys are probably the slowest way to accomplish something ever invented.) Anyways, I figured I could automatically install all my drivers like when originally installing Ubuntu or like you can do in Windows. Long story short, I can't figure out a way to do this or even figure out a way to manually install the drivers. The nearest thing, the "Additional Drivers" application, doesn't appear to even open. I'm still new to relatively new to Ubuntu, have only used the terminal a few times (and successfully used it even less), and am really hoping for a simple solution. Any help is greatly appriciated.

---

### Post by 2F4U on 2013-06-29
It is unlikely that overheating removes any drivers that were previously installed. Are you sure that the overheating did not damage some hardware components? The system log file may give you more information about why several hardware is no longer working.

---

### Post by Mark Phelps on 2013-06-29
It's tough to not think the "windows way" -- where you spend a lot of time hunting around for drivers and installing them.  But in Linux, you don't do that.  Installing drivers manually here can be a LOT of work -- because you often have to MAKE the driver, from source code.

Additional Drivers is not a general purpose driver installing utility; instead, it's a way of installing "restricted" drivers that don't get installed automatically during setup because installing them requires your permission.

If the machine crashed suddenly while running, it's more likely that the filesystem got corrupted; it's not going to uninstall drivers by itself.

What you will need to do is boot the PC from Ubuntu install media (DVD or USB stick) and follow the directions in the link: [http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html]("http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html")

---

