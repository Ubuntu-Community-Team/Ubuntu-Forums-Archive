---
title: "Problem in dconf-editor"
date: 2013-02-04
forum: General Help
---

### Post by anupamd on 2013-02-04
I want to change my selected background from orange to blue.

i installed dconf-tools.

i opened the dconf editor. But as soon as i hit enter after putting my desired values under gtk-color-scheme,  in org=>gnome=>desktop=>interface, my computer just FREEZES...


what is the problem.

Please help.

Thankyou

---

### Post by mc4man on 2013-02-04
Don't know why it freezes but would try 3 things - 
reboot & try again
reboot & open dconf-editor in a terminal & try
use gsettings or dconf command to enter the schema/key value(s) - ex. of what I use here on new installs for 2 colors

```
gsettings set org.gnome.desktop.interface gtk-color-scheme "selected_bg_color:#DCBE89;selected_fg_color:#3c3b37"
```

---

