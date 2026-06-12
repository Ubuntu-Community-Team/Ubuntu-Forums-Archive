---
title: "100% CPU while trying to change wallpapers, doesn't work right"
date: 2008-06-06
forum: General Help
---

### Post by rainwalker on 2008-06-06
When I right-click on my desktop and choose "Change desktop background", the Appearance window pops up like it should but changing the wallpapers doesn't work right. Not only does CPU load shoot up to 100%, but when I click on another image to set it as my wallpaper, it usually doesn't work. I have to click rapidly 4 or 5 times before it will set it. I've tried removing some of the wallpapers in the list so it doesn't have as many to manage and that hasn't helped.
Changing aspects of the theme is fine, though, it's just wallpaper changing that doesn't seem to work right.

Any ideas?

---

### Post by macstevejb on 2008-06-06
You will also note high cpu usage when opening the appearance pref and attempting to change themes, fonts etc.

There is a fix in the proposed updates repository.

Just open synaptic then updates tab then check the proposed updates box, reload the list and download and install any new updates that appear (THERE MAY BE MANY)

The fix centers particularly around any new gnome updates but I downloaded all updates without incident and this problem subsequently disappeared.

---

### Post by rainwalker on 2008-06-06
Well the strange thing is that it just started happening today.
Switching wallpapers is the only time CPU load spikes for me

---

### Post by maxol on 2008-06-06
Same problem [here]("http://ubuntuforums.org/showthread.php?p=5112600#post5112600").

---

### Post by xfacta on 2008-11-04
I had a similar issue in 8.04: high CPU usage whenever I open the Appearance Preferences panel and try to change settings. Not all settings would apply and the previews weren't working in "Customize".

1. Use the Processes tab in System Monitor to kill any running appearance... thingies. Another one starts for each time you try to change appearance settings.

2. I used Nautilus to browse to /home/username and did View -> Show Hidden Files (Ctrl+H)
Find file **.gtkrc-2.0** and rename it to **.gtkrc-2.0_old**

3. try Appearance Preferences now, should be good.

---

