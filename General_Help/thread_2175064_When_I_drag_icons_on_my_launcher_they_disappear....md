---
title: "When I drag icons on my launcher they disappear..."
date: 2013-09-17
forum: General Help
---

### Post by manatya on 2013-09-17
Dear all,

after installing some updates recently, I cannot drag and drop icons on my Ubuntu launcher. Well, I can drag them, but as soon as I "drop" the icon, it disappears. However, Desktop Switcher and Trash icons are permanently there.
When the program is running, e.g., Firefox, the icon is there, but as soon as I close Firefox - it disappears. If I right-click and choose "Keep in the launcher" - the icon again disappears immediately. 

I have tried several times unity --reset; unity --reset-icons; dconf reset /org/compiz/ , but the problem is still there. Unity Plugin in CompizManager is activated. Thank you so much for all your help!

---

### Post by CeejRab on 2013-09-17
Hello Manatya,

I can't think of anything off hand that could help you other than what you've tried with the unity reset etc... If I think of something I'll get back to you! Hang in there, somebody should be able to solve this for you soon.

All the best

---

### Post by manatya on 2013-09-18
Thank you, CeejRab, still waiting for any suggestions. I figured out today also that shortcuts that I create on the desktop do not function as well..

---

### Post by manatya on 2013-09-18
Problem resolved!

I followed suggestions from the previous post:
[http://ubuntuforums.org/archive/index.php/t-2031146.html](http://ubuntuforums.org/archive/index.php/t-2031146.html)

to reset all compiz settings to default!


1) First do a backup 

gconftool --shutdown
killall -r -I gconf
killall -r -I dconf
tar czf confbackup.tar.gz .compiz* .gconf* .config/dconf/  .config/compiz*

rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*

2) Reboot your system to see if everything its ok now.

---

### Post by CeejRab on 2013-09-18
Glad to hear it! Sorry nobody stopped by with anything sooner, but good job on the find and fix! 

All the best,

---

