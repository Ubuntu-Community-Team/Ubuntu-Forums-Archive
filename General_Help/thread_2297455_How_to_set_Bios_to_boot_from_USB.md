---
title: "How to set Bios to boot from USB"
date: 2015-10-03
forum: General Help
---

### Post by gordon33 on 2015-10-03
Hello all

Can my bios in  HP 15-r031ds lap top be set up to boot from a USB stick?  If so what am I missing?  I set USB as the first bootable.

Duel boot gone no Ubuntu so a previous thread [http://ubuntuforums.org/showthread.php?t=2297249](http://ubuntuforums.org/showthread.php?t=2297249) suggested [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 


I have been unable to get the USB with the  Boot repair program to be recognized.

Gordon

---

### Post by NM5TF on 2015-10-03
if you are asking how to set your BIOS to boot from the USB stick, this is how most PCs do it now...

reboot....wait for the initial boot screen, then press a special key to bring up the BIOS menu....on my
Dell it is the F12 key...your HP should have something similar....you will get a drop down menu where
you can select the USB stick as 1st boot device...

when you said that you "set the USB to be the 1st bootable" how did you do that if not by the above
procedure ???

has the boot-repair USB been used successfully before ???

---

### Post by yancek on 2015-10-03
When you boot the laptop and see the HP logo, you should see a message briefly at the bottom of the screen telling you which key to press to enter setup.

---

### Post by oldfred on 2015-10-04
I have seen these posted for HP. But may depend on model.
 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 

If you have secure boot on, better to have it off.
And/or you may have to in UEFI/BIOS, turn on or allow booting from USB ports.

---

### Post by gordon33 on 2015-10-04
Hello All

Choosing the second option from: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) helped correct the original problem.  It seems booting from a USB stick can be a challenge.

Well I gave up i want to thank those who responded.


Gordon

---

