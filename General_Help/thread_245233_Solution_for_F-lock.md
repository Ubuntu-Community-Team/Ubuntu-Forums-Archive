---
title: "Solution for F-lock"
date: 2006-08-27
forum: General Help
---

### Post by BoyOfDestiny on 2006-08-27
Updated (pieced from here [http://www.linuks.mine.nu/debian-faq-wiki/OtherHardware](http://www.linuks.mine.nu/debian-faq-wiki/OtherHardware)):

If you have a logitech keyboard modify the line
with setkeycodes 

to

setkeycodes e03b 59 e03c 60 e03d 61 e03e 62 e03f 63 e040 64 e041 65 e042 66 e043 67 e044 68 e057 87 e058 88

Script tested on MS natural keyboard (works 100%.)

Instructions here:

Pieced together from [http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

Download the script I uploaded here, extract it in your home directory (for simplicity)

#Open a terminal, 

sudo chmod 777 screw_f-lock
sudo cp screw_f-lock /etc/init.d/
sudo update-rc.d screw_f-lock defaults 99

Reboot.

This solved it for me, all F-keys work as they should. No problem with key combos (I use dosbox, so I need those F-keys). Best of all, I no longer have to toggle the F-lock key to use print screen (i.e. when f-lock was on, print screen became insert???).

Enjoy, should work on MS and logitech keyboards (although only tested MS).

Feedback appreciated.

---

