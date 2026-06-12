---
title: "Cannot Install"
date: 2015-03-24
forum: General Help
---

### Post by zubbs1 on 2015-03-24
Using a usb drive to install Ubuntu LTS 14.04.  I get the purple screen with 5 dots and it sticks there indefinitely.  I understand this is likely due to graphic driver issues until its fully installed and those drivers are set.  I understand to do this, I need to select 'nomodeset' from an advanced install menu.  However, I have no ability ability to get to that advanced menu.  Ive read the following link:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I never get a screen with any graphics at the bottom center, when I am supposed to 'press any key' to bring up the menu to then press f6 to get to a nomodeset option.  

The only think 'abnormal' is when I first boot up from the usb to get to the grub menu it briefly shows a message 'cannot load' but I never see the rest of the message as its way to fast.  

Is there any way to manually set the nomodeset from somewhere in the grub menu since it has options for command-line or editing commands?

Im totally frazzled by this, and my main windows os is boinked, so I have no usability from my main desktop until I can get this working.  Any help would be appreciated.

---

### Post by Bashing-om on 2015-03-24
zubbs1; Hello;

Is this a UEFI capable system ?
If so, try:
Booting, and as soon as the firmware boot screen clears repeatedly hit/release the escape key -> language screen;
escape key to accept the default, -> boot options screen  -> F6 key ;
space-bar to select, tab to OK, enter to accept the "nomodeset" boot parameter.

Can you now boot to the GUI ?

[INDENT][INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

