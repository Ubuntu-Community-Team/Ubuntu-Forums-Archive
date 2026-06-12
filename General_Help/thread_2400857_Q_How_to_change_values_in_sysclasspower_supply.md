---
title: "Q: How to change values in /sys/class/power_supply ?"
date: 2018-09-11
forum: General Help
---

### Post by linuksguru on 2018-09-11
[COLOR=#000000][FONT=Helvetica]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]How to change values in /sys/class/power_supply, making them permanent between reboots ?[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]This doesn&#8217;t work when executed as root, get permission error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]echo 68000000 > /sys/class/power_supply/BAT0/capacity_full_design[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]chmod as root 
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]chmod u+w /sys/class/power_supply/BAT0/capacity_full_design
[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]works only until restart, then permissions and value  change to default.

[/FONT][/COLOR]
 [COLOR=#000000][FONT=Helvetica]May be is possible to set it in?[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]/etc/sysctl.conf[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]Thanks in advance for any help.[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]Andrei[/FONT][/COLOR]

---

### Post by SeijiSensei on 2018-09-11
Add the command to /etc/rc.local. (You may need to create this file on recent Ubuntus.  Make sure it's executable by root.)

```
sudo touch /etc/rc.local
sudo chmod u+x /etc/rc.local
sudo nano /etc/rc.local
```

This is the last script to run during boot.

---

### Post by linuksguru on 2018-09-11
[FONT=arial]Thanks for suggestion, SeijiSensei.

Unfortunately, [COLOR=#000000]this doesn't work even after changing permissions (with chmod u+w), something blocks this /sys/class variable from being modified even by the root.

*echo 68000000 > /sys/class/power_supply/BAT0/capacity_full_design*[/COLOR][/FONT]

[FONT=arial]PS. Seems like even [COLOR=#008000]chattr[/COLOR] can't change attributes of these files.
lsattr: Inappropriate ioctl for device While reading flags on[/FONT]

---

