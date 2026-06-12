---
title: "USB not booting on other computers."
date: 2014-09-26
forum: General Help
---

### Post by sphinx2 on 2014-09-26
I have successfully(at least I think I have) installed Ubuntu to a flash drive, and my laptop will boot from it; however, when I tried to boot it on a different laptop, a blank screen with a blinking cursor on the top left appeared. The laptop I used to install Ubuntu to the USB was Windows 8.1, but the other laptop is Windows 7, is this the problem? If anyone knows what is wrong can they please help me?

---

### Post by oldfred on 2014-09-26
It could be video drivers. Then at grub menu you may need nomodeset or other settings. Did you install any proprietary drivers?

Or it could be whether your flash drive is BIOS or UEFI.

If flash drive is gpt partitioned you can do this:
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by henry-gerret on 2014-09-27
re-format the usb then burn on usb and open the usb run wubi in the drive and then there should be a thing help me boot from my computer it always works for me

---

### Post by sphinx2 on 2014-09-27
I have no problems booting it on my computer. I installed the full version of Ubuntu to the flash drive. It is not working when I try to boot into it on other computers.

---

### Post by oldfred on 2014-09-27
That does not help us with the issue. 

What are specs of other computer. Similar to current system or different video?

Can you hold shift key if BIOS or use escape key if UEFI to see if you get grub menu?
Can you boot recovery mode from grub menu or add nomodeset? Or if Intel video on of the other boot options?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

