---
title: "[SOLVED] Conky battery status"
date: 2008-07-05
forum: General Help
---

### Post by Kevbert on 2008-07-05
Hi. I have an Acer Travelmate laptop and Conky 1.4.9.  I'm having trouble getting the battery status to display.  I've tried a number of different combinations of the command, never get the percentage left to display.  This is the sort of command I've tried:
```
$color Battery: {$color #ec0000} $battery $color % remaining
```
and the error in terminal
```
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory
```
Also I want to display wireless quality as a bar.
Can anyone help ?

---

### Post by sayakb on 2008-07-05
Check here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by cammin on 2008-07-05
The wireless bar is easy **$wireless_link_bar**

The battery thing is most likely Ubuntu not recognizing your battery.

Seems to be a problem with Acers

---

### Post by sayakb on 2008-07-05
The battery info is in folder /proc/acpi/battery/C1BB and /proc/acpi/battery/C1BC
Try changing the path and see if it works.

---

### Post by Locutus_of_Borg on 2008-07-05
if in your /proc/ folder, our battery is BAT1 instead of BAT0, you have to append a designator to that command in conkyrc

i had the same problem and do not remember what i did as i now just have it displaying the output of "acpi -t | grep battery" but it is something like %battery(1) since it defaults to BAT0  you need to specify to use BAT1

---

### Post by Kevbert on 2008-07-06
Yippee... it now works.
I search for my battery status file and it is BAT1.  There's also BAT2, but I don't think that's used.  The command is
```
$color Battery: {$color #ec0000} ${battery BAT1} $color % remaining
```
The important thing is the curly brackets.
Wireless quality works with
```
$color Wifi Quality: ${color #07dbf4}${wireless_link_bar eth1}
```
Thanks to everyone that helped.

---

