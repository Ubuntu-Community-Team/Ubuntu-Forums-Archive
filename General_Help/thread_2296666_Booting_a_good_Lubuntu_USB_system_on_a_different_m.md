---
title: "Booting a good Lubuntu USB system on a different machine."
date: 2015-09-27
forum: General Help
---

### Post by Boyntonstu on 2015-09-27
I have a desktop Win 7 and I love the "dual" boot.

What I do is turn on the PC and hit esc. 

It asks where do I want to boot from?

I choose USB and click enter.

Walla Lubuntu!  I have 2 separate and independent systems.  

On my WIN 8.1 laptop if I hit esc I believe that it is asking for a windows bootable USB.  Something like UEFI?

What do I have to do to be able to boot Lubuntu from the USB?

---

### Post by DK1993 on 2015-09-27
What kind of computer are you using. With UEFI systems, you sometimes need to tweak settings in the BIOS setup screen to allow EFI USB Hard Drive support in order for you to boot Lubuntu. Also, some systems have different keys to get to the actual boot menu. Try F2, F8, F10, or F12 to try to invoke this screen.

---

### Post by Boyntonstu on 2015-09-27
> **DK1993 said:**
> What kind of computer are you using. With UEFI systems, you sometimes need to tweak settings in the BIOS setup screen to allow EFI USB Hard Drive support in order for you to boot Lubuntu. Also, some systems have different keys to get to the actual boot menu. Try F2, F8, F10, or F12 to try to invoke this screen.



My Lubuntu 14.08 resides on a 32 GB USB drive.

It works perfectly as described above.

I am typing on an HP2000 laptop, a very weak machine.  This is my reason for choosing Lubuntu.  Love it!

I changed the boot order in BIOS to USB and it bypassed it and booted into WIN 8.2.

I understand that Win 10 may be designed to block non-Window booting.

So far, it seems that Win 8.1 is making it very difficult if not impossible to choose a single click that Win 7 allowed.

Any ideas?

---

### Post by DK1993 on 2015-09-27
OP, this is a temporary workaround as it will not be seamless and easy to switch back and forth, but I would suggest turning OFF Secure Boot (Legacy Mode) and seeing if that allows the computer to recognize and boot into Lubuntu.

---

### Post by grahammechanical on 2015-09-27
If you installed Lubuntu on the USB stick using the Windows 7 machine then it may not/will not have the EFI boot files that are needed by the Windows 8.1 machine.

---

### Post by Bucky Ball on 2015-09-28
*Thread moved to **General Help**.*

---

### Post by Boyntonstu on 2015-09-28
> **grahammechanical said:**
> If you installed Lubuntu on the USB stick using the Windows 7 machine then it may not/will not have the EFI boot files that are needed by the Windows 8.1 machine.


Is EFI back compatible with a pre-EFI pc?

Do I need 2 USB Lubuntu OS?

Is it possible to add EFI to my stick?

---

### Post by sudodus on 2015-09-28
Yes it it possible but some installation methods may fail, and some systems may not survive updating/upgrading or system modifications from Windows.

You can make a persistent live system, that works in both BIOS and UEFI with mkusb. See this link

[mkusb#Persistent_live_systems](https://help.ubuntu.com/community/mkusb#Persistent_live_systems)

If you want a pendrive with a live and an ***installed*** system, that works in UEFI and BIOS mode, you can try [A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506).

---

