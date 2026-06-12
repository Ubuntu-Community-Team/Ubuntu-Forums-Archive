---
title: "Start a Command in Gnome at boot"
date: 2007-05-06
forum: General Help
---

### Post by DimitrisC on 2007-05-06
I am using Dapper for quite some time now on my Dell Inspiron 6000 notebook as my primary OS.  I also use beryl for about 6 months now and everything is working great.  The only minor problem I faced with my beryl installation was that the Caps Lock key and the combination of keys to turn my english keyboard to greek ( I am greek so I need to have greek keyboard support) alt - shift were not working under beryl.  I could change the keyboard layout using the applet in Gnome panel and I could write capital letters by holding the shift button but I couldn't using the alt-shift toggle or the Caps lock.

After searching the internet I found these commands that helped me get over the problem since when I run them in terminal the problems go away.

xmodmap /usr/share/xmodmap/xmodmap.gr
setxkbmap -model pc105 -layout us,gr -variant winkeys -option grp:alt_shift_toggle,grp_led:scroll

I tried making these commands permanent by entering them in startup programs  in system > preference > sessions but the problem is that sometimes the commands load and sometimes they don't.

Sometimes when i boot the computer and login I find that the caps lock and alt-shift combo work as they should and sometimes I have to enter the above commands in the terminal again to make it work.

Is there any other way to make these 2 commands start at boot everytime?

Thanks.

---

### Post by strabes on 2007-05-06
You could write a simple little bash script and add it to startup.

---

### Post by ebash on 2007-05-07
If you are using GNOME, try to see if the following will help: create a file named .gnomerc in you home account and add your commands there.

---

