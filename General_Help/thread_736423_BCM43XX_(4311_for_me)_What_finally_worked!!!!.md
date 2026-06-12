---
title: "BCM43XX (4311 for me) What finally worked!!!!"
date: 2008-03-26
forum: General Help
---

### Post by Darkrift on 2008-03-26
This is my second time isntalling kubuntu on my compaq v6210us laptop. The first time i spent literally 3 weeks (few hours a day) setting up my wifi with the help of freenodes #linux and #kubuntu. If you have tried tutorials trying to get a broadcom 43xx wifi card working and are having no luck, try this out.... you might get lucky!

Let me start off by giving some backround info. I am unable to boot from the livecd without the "apci=off" option on the kernel boot line. If I try i get a very odd plasma looking display bug with white/black/grey lines that "flow" around my screen (looks like those old fire plasma screensavers in black and white). Someone told me to use acpi=off and I had ever since. trying hundreds of methods to get my wifi working (every tutorial i could think of) and lots of users trying to help me all failed. Finally a user on irc told me to try adding "noapic nolapic" to my kernel boot params. I did this, and it seemed to get me farther but something was still working funny. He then asked what i had and when i showed him he told me to remove the acpi=off. It seems that whatever apci=off fixes, so does "noapic nolapic" because this worked along with the tutorial on here that has the "ndiswrapper-setup" script. 

One more thing that caused me headache. I had mistyped the "noapic nolapic" as "noapci nolapci" the first time when i added it to my "/boot/grub/menu.lst" and it failed. I then changed it and EVERYTHING worked perfectly (even other things that were not working that I was going to fix later like audio, cpu scaling and battery status). I ran the laptop like this all day with it doing great, then I had to reboot. After the reboot I got my display error again. I rebooted with acpi=off again thinking something had changed. After 2 more hours of messing around I realized that my menu.lst file had been "restored" from a backup somehow. I tested it and for some reason every time I booted menu.lst~ was being restored to menu.lst and it had bad settings in it. I edited both to be exactly the same so that the restore had no affect and now things are smooth again.

---

