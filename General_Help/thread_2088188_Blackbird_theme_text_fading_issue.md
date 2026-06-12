---
title: "Blackbird theme text fading issue"
date: 2012-11-25
forum: General Help
---

### Post by Kruger2147 on 2012-11-25
I really like the blackbird theme on XFCE, but I cant really use it because it only turns ***some*** of the backgrounds to the dark grey/black. Sometimes I get the light grey text over a light background, this usually happens in search fields or Ubuntu software Center. The weird part is, only some text is light grey, and some of it is black. Any idea of how to fix this? This theme has never worked, straight from install, on both 12.04 and 12.10

(I know this is GNOME 3, I'm messing around with it, but the symptoms are the same)

[IMG]http://i.imgur.com/x2dBi.png[/IMG]

---

### Post by rai4shu2 on 2012-11-26
Looks like this bug:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/913933](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/913933)

---

### Post by srphoenix on 2013-01-10
By try-and-error i found a workaround for this problem.

Start terminal and change to 
     /usr/share/themes/Blackbird/gtk-3.0/
Then edit the file "settings.ini" (I recommend to backup it prior to this.)
   sudo leafpad settings.ini
Find the entry 
   nfg_color:#e6e6e6
I changed it to 
   nfg_color:#808080

This seems to be a good compromise, because the menu items in the software center use the same color. So they won't be readable if you change to darker values.

Save the file. Then change to the Blackbird theme...

---

