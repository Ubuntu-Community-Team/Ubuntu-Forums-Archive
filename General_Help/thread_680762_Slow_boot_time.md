---
title: "Slow boot time"
date: 2008-01-28
forum: General Help
---

### Post by Cibola on 2008-01-28
I have Ubuntu and XP loaded on my computer. When I boot in XP takes less than a minute but to boot in Ubuntu takes 4-5 minutes. Is there abything that I may have loaded in the original setup that is causing this and can be removed??

---

### Post by Fangs on 2008-01-28
Are you able to enable a faster boot mode in your set up when you first turn the computer on? If so, then that should help. Also, if you have any programs running during startup, that will probably slow you down as well. You should be able to keep programs from running during start up that you do not want running during start up. Hope this boosts your start up speed!

---

### Post by ajgreeny on 2008-01-28
Where is the slow part of boot, POST, booting to the login screen or loading the GUI?  It would be useful if you boot up next time in text mode by removing the words "quiet splash" from the boot menu.  You can do it just for the current boot by editing menu.lst on the fly:-

1   At grub menu press "e" on the ubuntu OS you want to boot, usually at the top in a default menu.

2   In the text that appears go to line starting "kernel" and press "e" again.

3   Scroll to end of line with cursor key and delete "quiet splash" then press "enter" to save the change for this boot.

4   Press "b" to boot that OS  and a mass of text will scroll.  You should be able to see where the slowdown occurs and it may help remove the problem.

---

### Post by Cibola on 2008-01-28
If I hold alt F2 during boot it is fairly fast.. It appears to be showing all th steps. Whu would this be so much faster??

---

### Post by songo on 2008-01-28
1. on the terminal **sudo apt-get install bootchart**
it will install a small app that gives you a graphical chart of your boot.

2. reboot.

3. you can find a .png file in /var/log/bootchart. Now you can see what's retarding your boot. Fell free to paste it here.

What's is your screen resolution? and what resolution that your** /etc/usplash.conf** is set to?

---

### Post by Cibola on 2008-01-28
How do I find /var/log/bootchar?? Cant find it.

---

### Post by ajgreeny on 2008-01-28
You won't have it until you install **bootchart** as songo suggested, and then reboot.  That will produce the bootchart png.

---

