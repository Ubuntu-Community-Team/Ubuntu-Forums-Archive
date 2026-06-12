---
title: "Dual OS Boot (only some of the time?)"
date: 2014-08-08
forum: General Help
---

### Post by Silafu on 2014-08-08
Hey guys,
I run a Dual Ubuntu/Win system at home. I mostly use the Ubuntu and since I am a boot speed freak (ssd raid 0 and all), I'd really like to be able to run the boot loader only when I want to use windows (possibly thru a key shortcut or something similar, the way you need to hold Del if you want to enter bios).
Any ideas? Thanks in advance.

---

### Post by Cliff_Simonds on 2014-08-09
[SIZE=2]I found this[ here:]("http://www.upubuntu.com/2012/06/11-tips-to-speed-up-computers-running.html")[/SIZE][B]
6. Speed Up Boot Time By Disabling The Grub Boot Menu[/B]

When  starting your system, the screen will stop at the Grub2 boot menu. If  you want to disable it, you can follow these instructions:

- Open the terminal and edit this file on Ubuntu 12.04:
[INDENT]**sudo gedit /etc/default/grub**[/INDENT]
- For Linux Mint:
[INDENT][B]sudo pluma /etc/default/grub
[/B]- Search now for this line and set its value to zero:

**[COLOR=#cc0000]GRUB_TIMEOUT=[/COLOR][COLOR=blue]0[/COLOR]**

[CENTER][[IMG]http://1.1.1.4/bmi/3.bp.blogspot.com/-YTuaIc6H9xg/T-Se0U5dw8I/AAAAAAAAEXs/GEiSsr4tS3c/s400/grub2-config-file.png[/IMG]]("http://3.bp.blogspot.com/-YTuaIc6H9xg/T-Se0U5dw8I/AAAAAAAAEXs/GEiSsr4tS3c/s1600/grub2-config-file.png")[/CENTER]


-  Save the file and close it. Run  [COLOR=#ff0000]sudo update-grub[/COLOR] after. The Grub2 boot menu will not show up in the  next system rebooting, but you can call it by holding down the **Shift **key while rebooting.
It should still work.
[/INDENT]

---

### Post by Silafu on 2014-08-09
That sounds pretty cool, but what if I want to activate it after a Windows restart? I suppose the hold Shift method only works during a Linux reboot.

---

### Post by grahammechanical on 2014-08-09
If you do this and bring up the Grub boot menu to load Windows and then restart Windows the reboot will load Ubuntu unless you bring up the boot menu again. That is how you want it to work?

Grub is still there. The menu is still there. But the time that the menu stays on the screen has been set to zero. The 10 second delay is gone. The time it takes to press enter to load Ubuntu (first in the menu list) has gone. And that is how it seems to speed up the loading of Ubuntu.

---

### Post by Silafu on 2014-08-10
Do I hold the shift button during xkill or during boot-up?
If it is after, that means that if I am using windows and need to reboot, I have to first boot into Linux and then press shift and then get the option to boot into windows. That will be a bit weird.

Ideally the key is held during bootup which gives you the grub and you can choose your os. And the default os set Linux.

---

### Post by Impavidus on 2014-08-10
When you boot again, the computer doesn't remember anything about what you did during shutdown. First the bios loads, it checks for a bootable hard disk and finds grub. Grub is loaded and at that moment you have to hit shift. Then grub will display its menu. If you don't hit shift, grub will not display a menu and will load Linux right away. It doesn't matter which system you were running before the reboot.

---

### Post by Silafu on 2014-08-10
I got it now. This is the perfect solution for me. Thank you all for the support.

---

### Post by Cliff_Simonds on 2014-08-10
@Silafu,
a little bonus information for grub settings···
To change default operating sysytem:

Find the line that contains GRUB_DEFAULT=0 and set it to GRUB_DEFAULT=x where x  is the index of grub menu item to which you would like to boot to by  default. Note that the menu items are zero-indexed. That means that the  first item in the list is 0 and that the sixth item is actually 5.  So to boot to the sixth item in the list, the line would read GRUB_DEFAULT=5.
  Additionally, if you want to use a kernel in the "Previous Linux  Versions" menu, you'll want to change GRUB_DEFAULT=0 to  GRUB_DEFAULT="2>x" (make sure to include the quotations), where x is  the placement of the old kernel on the sub-list (assuming the "Previous  Linux Versions" is third on the main list). Remember that the list  always begins counting at 0.
  Then build the updated grub menu.
  sudo update-grub

---

