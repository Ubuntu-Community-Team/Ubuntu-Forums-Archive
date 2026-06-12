---
title: "Grub Beta wont let me change OS"
date: 2015-03-15
forum: General Help
---

### Post by eric49 on 2015-03-15
Ok, So i am new to the Ubuntu community. I have been a windows user, currently using windows 8.1. After Having issues with a game I play with the 64 bit version of windows, I decided I wanted t give Ubuntu a try, I partitioned my hdd and used a dual boot set up.  I downloaded Ubuntu 14.04 Desktop. I used ubuntu for about a day, Needed to switch over to windows, I restarted my computer. When Grub loaded up,I tried selecting windows, but grub would not allow me to move the highlighted os(Ubuntu). I looked around some forums and found a command that a lot of people found worked. It was essentially an update to grub. After the update completed, I restarted my computer, and grub no longer had the purplish background it was a black, and still would not let me move to highlight windows. Now it would not let me hit enter to select Unbutu, I had to wait until it automatically loaded the highlighted OS after a set amount of time, I tried multiple keyboards, still nothing. Now here is the kicker, after updating grub, the gui after logging in no longer shows up, I hit CTL+ALT+F1 it asks for my log in information. I put my information in, and throws an error saying my login info is incorrect. So now my HDD is not usable, is there any way to load the gui with going into a terminal? Ive tried going to my BIOS boot menu but grub overrides it. Is there anything i can do, or am i going to have to wipe my hdd and do a fresh install?

---

### Post by oldfred on 2015-03-16
What brand/model computer & what video chip?

Best to see details. From your Live installer add Boot-Repair and post link to its summary report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

