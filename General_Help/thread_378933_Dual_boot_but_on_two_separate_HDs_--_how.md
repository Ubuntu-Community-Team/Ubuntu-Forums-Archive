---
title: "Dual boot but on two separate HDs -- how?"
date: 2007-03-07
forum: General Help
---

### Post by CaptSaltyJack on 2007-03-07
My cousin is interested in dual booting but he'd rather not reformat his WinXP drive.  So our plan is to put an additional HD into his computer and put Ubuntu on it.  The thing is, how does that work?  How will Ubuntu know where to install the Grub bootloader?  Will this work out properly in the end? (we don't want to run into any issues where he can't boot XP)

I found this:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

But I should mention both HDs are SATA.  There is no setting either of them master/slave/primary/secondary.  Makes things a little more confusing.

---

### Post by brianC on 2007-03-07
All i did was install a second drive , and Ubuntu did the rest. The grub loader lets me choose Xpp on C drive or Ubuntu on the D drive. Did this for both compooters and all was fine, no problems at all.

---

### Post by CaptSaltyJack on 2007-03-07
Wow, that simple?  Very cool

---

### Post by hfw on 2007-06-13
Wow, that sounds easy.  I guess I can assume I could do the same thing if I want to add a second Feisty Drive.  I already have one drive with feisty, but want to add another. (I want one to play with, my wife wants one that always works.  In the short time that I have been running Ubuntu I have crashed and reinstalled three time.  It's time to give her a drive that I don't try to customize.)

---

### Post by juantao on 2007-06-13
Yes. In both cases, Ubuntu will keep information about the existing installation, XP or Ubuntu, on the first drive and allow you to have it as one of your choices at boot time.

Be careful you don't accidentally install over the existing installation during the install.

Be careful and let grub install to the primary hard drive (hd0 or sd0). Only one of those hard drives can be bootable, so chose the first one and let grub install there.

Be aware that if all goes well and later you remove the second hard drive, grub will be confused (where'd it go?) and not boot your computer. If this happens on your XP computer you can restore the Windows boot sector by booting the computer with a Windows XP install disc in the CD drive and choosing 'Repair' when the black 'Recovery Console' screen finally loads, issue the command 'fixboot' (are you sure?) 'Yes' and remove the CD and reboot - you'll have your Windows computer back again. If this happens to your Dual Ubuntu box you can boot from an install disc (CD) and choose 'Repair' and then edit the /boot/grub/menu1st file commenting out the part about your (no longer there) second hard drive.

---

