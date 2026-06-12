---
title: "Ubuntu can't start up (Acer Aspire 2920Z)"
date: 2017-12-13
forum: General Help
---

### Post by jetbitz01 on 2017-12-13
[COLOR=#242729][FONT=Arial]I had an old Acer Aspire 2920Z which was by default, Windows Vista. I upgraded to Windows XP quite a couple years back. The computer however, could not start up after Windows announce that they no longer support Windows XP. (It keeps prompting of a Windows error and goes into a bootloop) I could not obtain any recovery disk and only recently did I felt like changing to the Ubuntu OS (Ubuntu 16.04.3 LTS). I did not know whether my computer was 32 or 64 bit so I downloaded both. I boot from an USB flash drive and it started up. However on grub, it showed a blinking cursor and did not further advance to the start up menu on both the 32 and 64 bit versions. Previously when I downloaded Ubuntu, it managed to get past to reach the start up menu. However, it glitched very badly and I cannot install the OS.[/FONT][/COLOR]

---

### Post by oldfred on 2017-12-13
If on line specs match it is dual Core duo and then early 64 bit.

I have similar Toshiba, now retired, but recent installed 16.04 just to see if it works. I always installed fallback/gnome-panel as Unity was too slow. But it was functional. You may want Lubuntu or other lightweight flavor. 

How much RAM?

       Lightweight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

Was Windows error really from a hardware error which you then still have?

---

### Post by leunam12 on 2017-12-13
Your computer may have hardware problems such as bad disk and/or RAM, better to check that first.

---

### Post by jetbitz01 on 2017-12-13
Hi, how am I able to check for hardware issues.

---

### Post by jetbitz01 on 2017-12-13
I am not able to check on how much RAM it has as it is not in the description menu nor can I boot up. Wondering if there is a possibility that it works on older versions so I downloaded a version which others said was workable. Now it states that [This is the Ubuntu Live CD ( I am using a TumbDrive ) Press F1 for help and advanced options. For the default live system, press ENTER] I pressed enter but it loads up to the blank screen with the flashing cursor. Will try Lubuntu and see if it works.

---

### Post by leunam12 on 2017-12-14
Can you boot from the USB or not? If you can, there is a utility called "Disks" where you can go and check the SMART data for your hard drive. If the hard drive has errors and/or re-allocated sectors or sectors pending re-allocation it is time for a new hard drive.

---

