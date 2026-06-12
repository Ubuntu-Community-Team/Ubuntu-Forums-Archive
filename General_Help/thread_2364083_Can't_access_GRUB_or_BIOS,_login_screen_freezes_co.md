---
title: "Can't access GRUB or BIOS, login screen freezes couple seconds after boot"
date: 2017-06-18
forum: General Help
---

### Post by arkostin01 on 2017-06-18
Hiya!

Booting my machine happens as follows;

1. Initial black screen
2. *Very* brief Dell logo (where you would normally have the option to access BIOS, unable to do so even with the spamming of correct keys.)
3. Longer black screen (Where you would normally hold Shift/Esc to start GRUB, pressing either key causes the black screen to last indefinitely.)
4. Brief Purple screen followed by Ubuntu Login screen (Cursor does not show, neither mouse nor keyboard work and the whole screen freezes after ~6 seconds.)

After the sequence above, I have no option but to manually shut down my machine.

System info:
* OS: (Originally Windows 8, still on there but cannot access due to not being able to access BIOS or GRUB), Ubuntu 16.04
* Machine: Dell Inspiron 15 5000

If anyone has any (Really, any at all) clue as to what's happening or a possible fix, please provide your thoughts.

Thanks :)

---

### Post by ajgreeny on 2017-06-18
Is this a recent problem following installing Ubuntu or has it been a problem for some time?

If you can boot to a live USB or DVD do so and then see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by oldfred on 2017-06-18
UEFI has a fast boot setting which is totally different than Windows fast start up.
Fast boot assumes you have made no system changes, so what previous boot wrote to hard drive in the way of hard ware devices is totally the same. But then no time to press any keys.

Often total cold boot works. Or full shutdown of system and remove power, if laptop remove battery, and hold power switch to drain all remaining power for about 10 sec or so. Then boot and press correct key(s) to get into UEFI.
Fast boot also assumes you get back into UEFI from Windows. Grub now also has an entry to get into UEFI from grub menu, last in normal list before other systems.  'System setup' entry.

If not you have to open case & either jumper pins or remove motherboard battery. If you remove motherboard battery that resets everything to defaults and most systems require several UEFI settings changes.

---

### Post by arkostin01 on 2017-06-18
Inserting the live USB which I used to install this version of Ubuntu does nothing, I faintly remember setting the hard disk as the first priority in the BIOS boot settings, and since I can't get into BIOS settings I don't see any way for me to boot on USB.

---

### Post by arkostin01 on 2017-06-18
First of all, thanks for the advice guys, this seems to be a step or two in the right direction.

I completely powered off my laptop, disconnected the battery, and then held down the power button for ~10 sec. Spamming the BIOS setup/GRUB menu keys during the subsequent boot did nothing, however the Dell logo flashed three times now (!) instead of once before continuing to the login screen and freezing, almost like it tried to go into BIOS but instantly left it before showing any graphic signs. 

I figure if I can disconnect the CMOS battery for a few minutes like you said, it might allow me to get into BIOS, then subsequently boot onto USB so I can gather some data about what's happening to GRUB on boot. I've taken my laptop apart and am typing this out as my CMOS bat is disconnected and sitting on my lap. 

Going to put everything back together and try to get into BIOS now, will post whether or not it worked soon.

---

### Post by arkostin01 on 2017-06-19
After putting the whole thing back together and starting it up, I was finally able to boot into BIOS. From there I didn't change any settings, just to be safe, and booted normally out of BIOS. Somehow, I booted into my Windows install (Which I haven't been able to boot into since I first tried installing Ubuntu). Currently having no issues other than my keyboard not being backlit (minor), will try to boot into Ubuntu after some quick file backups.

Seems very promising, again thank you guys :)

---

