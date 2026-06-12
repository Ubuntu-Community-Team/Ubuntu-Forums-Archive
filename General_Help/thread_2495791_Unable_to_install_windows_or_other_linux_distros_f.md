---
title: "Unable to install windows or other linux distros from boot"
date: 2024-03-01
forum: General Help
---

### Post by ibrahimnneto on 2024-03-01
Hey guys, ive been struggling with this for the past 2 weeks with almost no success, tried asking for help on reddit and followed every single tutorial out the but nothing worked... Since i finally got to atleast install mint, hope someone here can help me figuring out confused is going on

Quick breakdown of what happened:
Bought a Dell g15 5510 for my little brother that came with ubuntu since hes used to windows we installed Windows on the notebook with no problem at all

almost a year later i wanted to "reset" the notebook so i formated it, but was unable to install windows after doing that, with the exact same usb/iso that i did the first time so i thought maybe its just a one time thing and installed ubuntu with the purpose of installing windows soon after

Turns out i was unable to even get to the installer in boot. Tried literally every single method out there: ventoy, windows media creation tool, rufus, oldschool formating the usb and pasting the ISO, different ISO`s, different USB`s with different sizes and also 3.0 3.2 and 2.0

Tried countless settings on the bios, disabled/enabled secure boot, fast boot etc but nothing worked. (i must have tried like 40 different setup and installations so i gave up on windows)

After that, decided to atleast go with mint since it looks similar to windows and would be easier for my brother to use, but also couldnt install it in any possible way just like with windows, tried everything.

With mint i got through the boot, it showed the mint logo but it started as ubuntu and the onlhy thing i got was an empty mint folder on the desktop, no installer or anything

After hours of searching the mint forum i found an user with the EXACT same problem as me (with the mint installation, he sadly didnt mention windows), like every single thing was the same as i was going through, even same notbook if im not mistaken (trying to find it to link here) and he "solved" the problem by installing debian and after that, installing mint. (Some guy later said it was probably a GRUB problem, it was getting confused with 2 ubuntus in the boot or something like that and it could have been solved by installing REEFIND, but since i was sucessfull with debian, didnt try that. just adding for the most details possible).

And it worked! I installed debian and then i was finally got to install mint, no problems at all with both installations.

So i was like "Maybe it was some weird ubuntu settings and now i can install windows on mint" but i got the exact same results..

After all that i decided to get the Dell recovery ubunut 20.04 iso with all the factory drivers to see if it was some special dell setting, so im back at ubuntu but same result..

Idk what to do at this point, but it shouldnt be impossible, right?

unless its possible to have some sort of hardware problem that makes it unable to install windows only? Anyone has any idea what could it be?

Thanks for any replies, im here and willing to give all information needed if asked!!

---

### Post by ibrahimnneto on 2024-03-01
Just some more info since im struggling with this for week, didnt want to make the post a huge wall of text:

NEVER got to the windows installer at all, always just stuck on the dell logo untill it eventually just boots into ubuntu/mint;
Only got to anything related to windows 2 times. I literally tried every combination of settings possible on the bios, playin around with the secure boot settings, reseting the bios to factory and reseting the keys, i finally got something related to windows

[COLOR=#333333][FONT=&quot]i got a different screen in the boot, After reaching dell logo, the notebook did a loud BEEP and displayed the message "operating system loader signature not found in Secure Boot database ('db'). All bootable devices failed Secure Boot verification"

[/FONT][/COLOR][COLOR=#333333][FONT=&quot]it seemed like an easy solve, just enabling the secure boot options etc but it didn't work and i got the same message, so i started googling solutions to this message and i found this, which seems to have solved it for a lot of people:

> [/FONT][/COLOR][I]1. On Startup, press F12
2. Reset Bios to default settings
3. Restart laptop
4. In Bios, select Boot Sequence menu
5. Manually ADD additional line with the name "Windows Boot Manager"
6. Select /EFI/BOOT/BOOTX64.EFI
7. Exit[/I][COLOR=#333333][FONT=&quot]

[/FONT][/COLOR][COLOR=#333333][FONT=&quot]So i followed the steps and this time, i got to a windows screen, BUT it was a blue screen of death with this error: [/FONT][/COLOR][COLOR=#333333][FONT=&quot]Driver PNP Watchdog,
[/FONT][/COLOR][COLOR=#333333][FONT=&quot]It seems related to some hardware issues(?)

I also noticed my GPU isnt recognized by ubuntu or the bios, but i dont think it ever recognized it, afaik its a very common issue with ubuntu/nvidia and the graphics card only some stuff behind the scenes or something like that. BUt could the GPU being dead somehow cause all of this?


[/FONT][/COLOR]

---

