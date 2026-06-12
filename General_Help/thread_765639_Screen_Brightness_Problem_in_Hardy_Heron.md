---
title: "Screen Brightness Problem in Hardy Heron"
date: 2008-04-24
forum: General Help
---

### Post by jwwadk on 2008-04-24
Hello all, apologies if this sounds like a noob-ish question. I upgraded to Hardy today from Gutsy, and my screen seems very dim. My computer is an Asus M50sv-a1 laptop dual-booting with Vista, and it has shortcut keys for adjusting the brightness. Using Gutsy, these shortcut keys worked just fine (they're Fn+F5 and Fn+F6) and adjusted my brightness accordingly. However, they do nothing using Hardy. I looked at Power Management and the options for adjusting screen brightness seems to have disappeared, and the /proc/acpi/video/VGA/LCDD/brightness trick refuses to work for me. As it is, I'm straining to see my screen, so any help would be greatly appreciated.
Thanks

---

### Post by Backdraft on 2008-04-24
I'm having the same issue.  The brightness applet says "cannot get laptop brightness" as well.  The Fn + F9/F10 worked up until the upgrade.

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by jwwadk on 2008-04-25
Thanks! It worked perfectly!

---

### Post by jwwadk on 2008-04-25
One thing, though. On my machine it was asus-laptop and NOT asus_laptop. However, ls_switch is correct.

---

### Post by don bohrer on 2008-04-25
Hi guys, I am experiencing several display issues with hardy. One of which is the brightness on a dell gx110 desktop. The desktop is darker, video's on youtube, myspace are also affected. I juacked up the brightness of the monitor but no success.

don

---

### Post by moeFinley on 2008-04-26
I have the same issue with a Adevent 8212.  I don't think it has a light sensor on it?

---

