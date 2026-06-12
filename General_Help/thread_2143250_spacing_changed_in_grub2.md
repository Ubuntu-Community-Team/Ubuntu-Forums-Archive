---
title: "spacing changed in grub2"
date: 2013-05-08
forum: General Help
---

### Post by gilloz on 2013-05-08
After downloading and installing my last update of Ubuntu 12.04, I notice that my grub2 menu now has double spacing between each letter which widens the menu on the screen.  How do I go about reducing it to a normal text menu?

---

### Post by dino99 on 2013-05-08
[http://ubuntuforums.org/showthread.php?t=1555358](http://ubuntuforums.org/showthread.php?t=1555358)
[http://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised](http://unix.stackexchange.com/questions/31672/can-grub-font-size-be-customised)

---

### Post by oldfred on 2013-05-08
May be font, but probably video mode. Maybe it now is using 640x480 where your screen is double that?

Grub tries to use video from system now. Is this uncommented, no # ?
#grub's set gfxmode=640x480

 cat /etc/default/grub

Have you installed nVidia drivers or did update not reinstall them?

---

### Post by gilloz on 2013-05-08
Thanks guys for your responses.  I installed a program Grub Customizer and made changes to the fonts and resolutions and got it looking half way decent, but the border lines are dashes as oppose to solid lines and there are still spaces between letters still making it wider on the screen.  I have the resolution set at 1026x760 with a font of 16.  I even tried using the method of installing a Ubuntu 12.04 disc and see if I could transfer the grub2 menu, but that didn't work.  The menu is usable, but does not look nice.

---

### Post by gilloz on 2013-05-09
The Grub2 menu would look better if the border lines surrounding the menu entries were solid lines and not little question marks in boxes.  What do I need to change to get rid of these question marks and replace them with solid lines?

---

### Post by oldfred on 2013-05-09
I have not used grub-customizer, but I think it may change scripts?

Do not know details of scripts but this has some info on customizing grub.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

