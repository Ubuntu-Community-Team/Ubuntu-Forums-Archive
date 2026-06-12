---
title: "Ubuntu Dual Boot with Windows 8.1"
date: 2015-08-26
forum: General Help
---

### Post by legoclone09 on 2015-08-26
I just re-installed Ubuntu 14.04 (unfixable login loop), and I can not switch back to Windows. I still have my Windows install, but I am not greeted with a screen to switch OSes on start-up.

---

### Post by Petro Dawg on 2015-08-26
When I run into that kind of thing I usually just live boot with an Ubuntu disk or USB and install/run [boot-repair]("http://ubuntuforums.org/help.ubuntu.com/community/Boot-Repair").  It is usually the easiest fix for those kinds of situations.  If the Windows boot loader got deleted you might need to run a windows boot repair utility as well.  That is about all I can recommend at the moment without knowing the specifics of how you did the install.

---

### Post by legoclone09 on 2015-08-26
> **Petro Dawg said:**
> When I run into that kind of thing I usually just live boot with an Ubuntu disk or USB and install/run [boot-repair]("http://ubuntuforums.org/help.ubuntu.com/community/Boot-Repair").  It is usually the easiest fix for those kinds of situations.  If the Windows boot loader got deleted you might need to run a windows boot repair utility as well.  That is about all I can recommend at the moment without knowing the specifics of how you did the install.
I have done that, but when I reboot, I only get Ubuntu, advanced setup, and the system setup. No Windows 8.1 (dev_sda1)

---

### Post by Petro Dawg on 2015-08-26
What happens when you run the following in terminal... 

[SIZE=2][FONT=arial]> [COLOR=#111111]sudo update-grub[/COLOR][/FONT][/SIZE]

---

