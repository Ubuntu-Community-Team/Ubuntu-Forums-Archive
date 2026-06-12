---
title: "Dual boot Window 8.1 and Ubuntu, in HP nb"
date: 2014-09-11
forum: General Help
---

### Post by crystal3 on 2014-09-11
With pre-installed Windows 8.1 in HP (64-bit), I successfully installed Ubuntu 14.04 in my notebook. I can boot Ubuntu. However, I cannot boot Windows 8. Thus, I wanna know how to make a boot option page before booting any operating systems? Thanks!

---

### Post by Bucky Ball on 2014-09-11
Welcome.

Boot Repair is your friend:

Get BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Use the 'Recommended Repair' option. Good luck.

---

### Post by oldfred on 2014-09-11
If you are only booting Ubuntu, you may have installed it in BIOS mode. Windows is in UEFI mode and the two modes are not compatible.
You should be able to use the one time boot key to choose which system to boot, but cannot configure grub to change boot modes and boot Windows.

Most HPs only boot Windows in UEFI mode and require work arounds to boot Ubuntu from UEFI. Then you can also configure grub to boot Windows.

Post link to BootInfo report that Boot-Repair creates, so we can see details.

        
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

