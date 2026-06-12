---
title: "[SOLVED] Feisty screen brightness when using battery"
date: 2007-04-30
forum: General Help
---

### Post by Kristopher on 2007-04-30
When i unplug the power supply from my laptop the screen brightness decreased, i feel its a little too dark is there a way to increase the brightness when i am not using the power supply?

---

### Post by mcduck on 2007-04-30
System/Preferences/Power Management and set the brightness you want on the 'On Battery Power'-tab :)

---

### Post by Kristopher on 2007-05-01
I dont have that option i only have 

sleep when inactive
display sleep when lid closed 

etc just 4 options nothing there that says brightness?

---

### Post by Kristopher on 2007-05-01
How do i enable that option?

---

### Post by mcduck on 2007-05-01
It should be there. Perhaps your display just doesn't support such feature?

---

### Post by teachop on 2007-05-01
There is no option like that in my Feisty either.  There are just a few adjustments possible from that interface.

But I found if you run "gconf-editor" from the terminal, and do an Edit Find for "power", then click on /apps/gnome-power-manager, there are lots of options.

There is an option there called "battery_brightness" that is set to 70 on my machine, and can be changed.  Perhaps raising that will do the trick.

---

### Post by Kristopher on 2007-05-02
Thanks teachop, i tried that changed the brightness to 100 and the same for the keyboard, did a restart and its just the same i cant see any difference. Would this be that my laptop doesnt support this feature? or that Ubuntu doesnt do that for my type of laptop?

I have a HP Pavilion 6000 series if that helps.

---

### Post by mcduck on 2007-05-03
What happens if you add the Brightness Applet to your panel (Right-click on empty space in your panel, select 'Add to Panel, find the applet and drag&drop it into your panel). Can you change the display brightness with that one?

Also, check your /etc/X11/xorg.conf. Do you have DPMS enabled in your monitor section?
```
Section "Monitor"
	Identifier   "ASUS LCD"
	Option	    "DPMS"
EndSection
```

edit: also check if you have any options for the display in your laptop's BIOS..

---

### Post by Kristopher on 2007-05-03
Hi mcduck,

I will check all that when i get home, oh where do i find the "Brightness Applet"? is it pre-installed? sorry but i am a new user (1 month) using Ubuntu as my main OS.

With regards to the xconf file do i edit it (if its not there) to have DPMS?

Regarding the image you attached the "Set display Brightness to" is not displaying on my Power management settings on any of the tabs AC, Battery and General.

---

### Post by kilou on 2007-05-03
same for me with an MSI S260 laptop. I don't have the brightness slider in the Gnome power managment applet and if I change the value of battery-brightness to 1 (ac_brightness is set to 100) there is no difference. In all situation when I unplugged AC the screen just dims by 2-3 notches...

However the Fn+F4/F5 can change brightness manually so there is certainly a way to do this with a script that would mimmick the action of these as an acpi event! Probably we need to add a script in /etc/acpi/battery.d and /etc/acpi/ac.d that would simply lower the brightness when switching on battery and increasing it when going back to AC. All we need to figure out is how are the Fn+F4 and Fn+F5 command translated and what they do run for scripts so that we can ask to run X times the script that lower the brightness by 1 notch etc. I'm sure there is a way to achieve this since the function keys DO work for most of us! Please help a newbie know what is the script invoked by these Fn+F4 and Fn+F5 keys :)

---

### Post by Kristopher on 2007-05-03
"Fn+F4/F5" -     Fn?

---

### Post by kilou on 2007-05-03
Fn is a Function key on laptops t be used in combination with other keys to activate specific stuff like LCD brightness, volume or even put computer to sleep. It's like pressing Ctrl+something else except that you use a key badged Fn instead of Ctrl.

---

### Post by kilou on 2007-05-03
I could solve the problem on my MSI S260 laptop by loading the kernel module msi-laptop with option force=1 (add msi-laptop force=1 to the /etc/modules list and reboot. If you just want to test type sudo modprobe msi-laptop force=1). Then I can command the screen brightness with

echo "n" > /sys/devices/platform/msi-laptop-pf/lcd_level

replace n with 0 to 8 (0=dark, 8=bright)

Then simply create 2 scripts:
In /etc/acpi/battery.d/20-brightness.sh
#! /bin/bash
echo "0" > /sys/devices/platform/msi-laptop-pf/lcd_level

In /etc/acpi/ac.d/90-brightness.sh
#! /bin/bash
echo "8" > /sys/devices/platform/msi-laptop-pf/lcd_level

I'm not sure about the 20 and 90 but it seems to work on my system.

---

### Post by mcduck on 2007-05-03
> **Kristopher said:**
> Hi mcduck,

I will check all that when i get home, oh where do i find the "Brightness Applet"? is it pre-installed? sorry but i am a new user (1 month) using Ubuntu as my main OS.

With regards to the xconf file do i edit it (if its not there) to have DPMS?

Regarding the image you attached the "Set display Brightness to" is not displaying on my Power management settings on any of the tabs AC, Battery and General.
Yes, the applet is pre-installed in Feisty (7.04) and you'll find it from the window that opens when you select 'Add to Panel' from the panel's right-click menu.

What comes to xorg.conf, yes, you could try adding the DPMS option if it isn't there by default. To edit the file open a terminal, run 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup' (to create a backup of the file) and then 'gksudo gedit /etc/X11/xorg.conf' (to open the file for editing). Add the line, save, close the file and reboot & hope for the best. ;)

(In the worst case, even if highly unlikely, that might result in your desktop failing to start if your display really doesn't support DPMS. Then just select the Recovery Mode from Grub menu when booting the machine, log in and run 'sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf' to restore the backup version you created. Then run 'reboot' to restart the machine.)

---

### Post by Kristopher on 2007-05-03
I tried the brightness applet but its got the no red circle "Cannot get laptop applet brightness"

Here is that part from the xconf

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

---

### Post by Kristopher on 2007-05-05
Ok very weird but i thought i would post that i got it fixed. Just tried today Fn + F8 and the brightness decided to increase so thats it just as bright when runing it with the battery WOOHOO dont know why it didnt work before......

Thanks for all the help.

---

