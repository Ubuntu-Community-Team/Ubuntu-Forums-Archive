---
title: "Problem with ractional scaling using xrandr"
date: 2018-10-31
forum: General Help
---

### Post by alepiazza on 2018-10-31
[COLOR=#242729][FONT=Arial]I just installed Ubuntu 18.04 LTS in dual boot with Windows 10 on my Thinkpad X1 Yoga 2nd gen which has a high dpi screen (2560x1440). Since the GUI settings do not permit fractional scaling (and 100% is too small while 200% is too big) I followed the intructions in  this page: [https://wiki.archlinux.org/index.php/HiDPI#Fractional_Scaling](https://wiki.archlinux.org/index.php/HiDPI#Fractional_Scaling).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]However, running the following command from terminal
[CODE]xarndr --output eDP-1 --scale 1.3x1.3 --panning 256ox1440[[/FONT][FONT=Arial, Helvetica Neue, Helvetica, sans-serif]/CODE]
[/FONT]I get pretty bad result[FONT=Arial] where the desktop is resized and I get black borders. Moreover I can drag windows in the balck borders but they leave a trace beheind[/FONT][FONT=Arial]. See pictures below.[/FONT]
[/COLOR]
[COLOR=#242729][FONT=Arial]I think it may be a conflict between xrandr and the Gnome desktop enviromment, but it's just a guess. Any suggestions on how to solve this bug?


[ATTACH=CONFIG]281499[/ATTACH][ATTACH=CONFIG]281500[/ATTACH][/FONT][/COLOR]

---

