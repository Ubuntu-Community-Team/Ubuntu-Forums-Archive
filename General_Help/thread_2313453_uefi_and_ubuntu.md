---
title: "uefi and ubuntu"
date: 2016-02-12
forum: General Help
---

### Post by wyndlass on 2016-02-12
i just got a hp pavilon g7-2017us(don't know specs yet). i want to put my ubuntu drive into it and i get uefi errors. how do i get around that?

---

### Post by grahammechanical on 2016-02-12
What were the errors? Is secure boot turn on?

---

### Post by oldfred on 2016-02-12
See also link in my signature for more info:
Other HP
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu.

---

### Post by wyndlass on 2016-02-13
i'll put the drive back in & write down the error ii get.

---

### Post by wyndlass on 2016-02-13
here's the error:

hd error

run hd test in system diagnostics

hd1 3f1


when trying to use notebook drive for booting it says no bootable device, insert bootable device and press any key.

---

### Post by oldfred on 2016-02-13
That is because you do not have a "Windows" UEFI boot. The no bootable device is from Windows. 
See links on all the other HP users and renaming/moving efi boot files.

---

### Post by wyndlass on 2016-02-16
i was thinking last night after seeing if i had a secure boot option in bios, don't, if i installed x64 wily on the g7 if that would work....

---

### Post by wyndlass on 2016-04-11
i just installed 15.10 over win 10.

---

