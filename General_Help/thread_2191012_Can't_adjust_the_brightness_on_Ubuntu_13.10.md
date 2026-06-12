---
title: "Can't adjust the brightness on Ubuntu 13.10"
date: 2013-11-30
forum: General Help
---

### Post by defense-curl on 2013-11-30
Hi everyone. I've got a new laptop ( Lenovo Thinkpad E145 ) and I can't adjust the brightness. I've found some solutions suggesting to edit the grub file, but none of them worked for me. Is there any other way to fix this problem? Thank you

---

### Post by germanix on 2013-11-30
Hi, I have a Thinkpad but not the same model as yours. On mine in order to adjust the brightness by using the buttons on the keyboard (on mine the F5 + F6 buttons), you have to hold down the Fn button at the same time (bottom left corner of the keyboard). Alternatively you can also adjust it in "system settings" then "brightness and lock". You are not very clear what you have tried so far so I am not to sure what your problem is. Anyway I have the Thinkpad X230 and everything works out of the box. I only have linux installed.

---

### Post by defense-curl on 2013-11-30
> **germanix said:**
> Hi, I have a Thinkpad but not the same model as yours. On mine in order to adjust the brightness by using the buttons on the keyboard (on mine the F5 + F6 buttons), you have to hold down the Fn button at the same time (bottom left corner of the keyboard). Alternatively you can also adjust it in "system settings" then "brightness and lock". You are not very clear what you have tried so far so I am not to sure what your problem is. Anyway I have the Thinkpad X230 and everything works out of the box. I only have linux installed.

Hi, actually my keyboard layout is different (which I'm not going through that). My problem is that I can't adjust the brightness anywhere! when I press the keyboards (on mine f7 and f8), I can see the window that appears top right corner which is showing that it is changing the brightness, but nothing happens. I can't even adjust the brightness in settings. 
I've searched the forum and it seems that many others had this problem on 13.10. I've tried to edit the grub file as suggested:
/etc/default/grub
and change the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" into GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
and then update the grub file and reseting the system, but this doesn't solve the problem.

---

### Post by defense-curl on 2013-11-30
I also tried to change the value of brightness file located in /sys/class/backlight/thinkpad_screen/brightness to the minimum possible number, but that doesn't work either

---

### Post by henu on 2013-12-04
I have the same laptop and the same problem. Anyone found a solution?

---

### Post by Juha_Peltoniemi on 2014-01-23
.

---

