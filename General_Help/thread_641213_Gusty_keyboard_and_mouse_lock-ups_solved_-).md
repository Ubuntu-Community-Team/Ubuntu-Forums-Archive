---
title: "Gusty keyboard and mouse lock-ups solved :-)"
date: 2007-12-15
forum: General Help
---

### Post by bristleburger on 2007-12-15
I have been frustrated by frequent keyboard and mouse lock-ups since installing Gusty one month ago.

These lockups would occur at random intervals during normal usage, but I could also lock my machine up to order using either Rhythmbox or Totem to play mp3 files. Closing the application during playback, or simply stopping playback resulted in an instant lock-up.

I have a USB keyboard and mouse which were connected to the PS/2 mouse and keyboard ports on my system unit using adapters that were supplied with the mouse and keyboard. This arrangement has worked flawlessly since 2005, using Dapper, Edgy & Feisty.

Since dispensing with the adapters and connecting the mouse and keyboard to USB ports rather than to PS/2 ports I have not suffered any lock-ups :-)

Perhaps Gusty has a problem with PS/2 ports?

I couldn't find anything obvious in the log files.

Additional info:

Just before the lock-up (during mp3 playback), the PC would become slightly less responsive – as if it was handling lots of interrupts. But after the lock-up, the PC would continue to work normally – even the screen saver would start as usual.

Using ssh to connect to the PC it was possible to restart GDM using “sudo /etc/init.d/gdm restart”. This would restart GDM as expected, but the keyboard and mouse would remain dead.

Hope this helps someone

BB

---

### Post by Psyphre on 2007-12-16
I have a problem with my keyboard and mouse locking up randomly. Except for me its the opposite, only when I used USB. My mouse is not plugged to ps/2 and works fine, but unfortunately my saitek eclipse 2 can only work with usb, so im stuck. Its really annoying cos i cant use ubuntu properly cos of this :(

---

### Post by Sef on 2007-12-16
> Since dispensing with the adapters and connecting the mouse and keyboard to USB ports rather than to PS/2 ports I have not suffered any lock-ups

Perhaps Gusty has a problem with PS/2 ports?

I use PS/2 for both and have no problems.  Could be a hardware issue or maybe the software did not install correctly.

---

### Post by bristleburger on 2007-12-17
Could be hardware, but I haven't had this problem before, so I suspect it's either Gusty related or due to a problem with the upgrade from Feisty.

I have also had some problems with networking recently whereby it was not possible to get a shh connection to or from any other machines on my LAN. Restarting with “sudo /etc/init.d/ssh restart” didn't help either. During this episode I found that ping times to other hosts on my LAN would vary wildly between a few ms and several seconds (normally I see a reasonably steady 0.2 ms).

Since setting a static IP address in /etc/network/interfaces, I haven't had any stability trouble – even running Compiz :-)

BB

---

### Post by Psyphre on 2007-12-17
i had this problem since edgy im afraid :(

---

### Post by bristleburger on 2007-12-17
Hi Psyphre

Which problem have you had since Edgy? Keyboard lockups or network manager?

BB

---

### Post by Psyphre on 2007-12-18
keyboard lockups. It will lockup randomly, could be 10 minutes, could be 5 hours, but its usually within the hour. What ever key I press at the moment that happens, will be constantly pressed.

---

### Post by bristleburger on 2007-12-18
Must be aggravating!

What keyboard settings do you have in xorg.conf?

I'm using these...

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105
EndSection


...and have configured the &#8220;UK keyboard&#8221; layout in System->Preferences->Keyboard

With these settings my keyboard works well. I found that attempting to set layout and variant options in xorg.conf like this...

Section "InputDevice"
        Identifier      "Generic Keyboard" 
        Driver          "kbd" 
        Option          "CoreKeyboard" 
        Option          "XkbRules"      "xorg" 
        Option          "XkbModel"      "pc105" 
        Option          "XkbLayout"     "uk" 
        Option          "XkbVariant"    "gb" 
EndSection 

...caused problems on my system.

BB

---

### Post by Psyphre on 2007-12-19
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Same as urs it seems. I'll try using ur settings but i dont think it has anything to do with the keyboard, i think its usb issues. The same will happen to the mouse if its on  usb (i switched it to ps/2 cos of this).

---

### Post by bristleburger on 2007-12-19
You're probably right, especially since you have had these problems since Edgy.

It could be BIOS related. I found that automatic resource configuration seemed to cause me problems so I have selected "resources controlled by" "manual" rather than "ESCD".

It might be worth testing the effect of other BIOS settings too (USB and keyboard settings). Best to only make one change at a time though ;-)

---

### Post by Psyphre on 2007-12-23
I found one solution, and that is to disable Legacy USB support. Works perfect now with no lockups. Unfortunately comes with a big downside, i can no longer use the keyboard in grub, so i cant boot into windows. Which is a big problem since there are a few things i need windows for. So its a temp solution.

---

### Post by bristleburger on 2007-12-23
Glad you found a solution Psyphre, but you certainly need a more permanent fix.

I wonder if this problem could be related to udev or something similar. If your feeling adventurous it might be worth compiling USB keyboard support directly into the kernel rather than relying on the correct modules to load when the system boots.

---

### Post by Psyphre on 2007-12-28
afraid im not very knowledgable with linux and would have no idea how to do that.
I did find this however:


"He reported having solved his problem by adding the following lines to the boot options in /boot/grub/menu.lst:

acpi=force irqpoll

(that would be right after the 'ro quiet splash' of your kernel description).

This way we can leave Legacy USB on in BIOS so we have USB keyboard support in grub which is always nice"

I will try it soon.

---

