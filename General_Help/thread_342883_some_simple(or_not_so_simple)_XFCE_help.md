---
title: "some simple(or not so simple) XFCE help"
date: 2007-01-20
forum: General Help
---

### Post by tpnerdcore on 2007-01-20
ok, i just installed  XFCE on a Duron 750mhz 256mb ram. Everything runs fine. I am so used to gnome that customization in xfce is kinda fishy. Here is what i would like to do:

Kinda replicate MAC OSX Finder. Have custom folders with custom icons in Thunar. I was thinking of making a folder in Home called "Music" with a custom icon and then have the "music" folder on the side pane. is that possible? sorry if my suggestion is kind of odd

-thanks
anthony

-----------------------
specs. (on Xubuntu computer)
AMD Duron 750mhz
256mb PC100 ram
30gb Quantum Fireball HD
ASUS(nvidia) TNT2 16mb Graphics.

---

### Post by kerry_s on 2007-01-20
You can kinda get it that way. You can put a emblem on it, add emblems to " /usr/share/icons/(theme)/(size)/emblems " then just drag the folder to the right to create a shortcut->

---

### Post by tpnerdcore on 2007-01-20
ahhh emblems....haha thanks alot. i appriciate the info. I like your icon theme by the way. Not really my style but it looks nice with the mac metacity.

thanks again.
-anthony

---

### Post by kerry_s on 2007-01-20
Yeah, i just use the stock "Rodent" theme for xfce. I just find it so much less distracting. I just like to keep it simple.

---

### Post by tpnerdcore on 2007-01-20
your answer seems very simple, but for some reason i am doing something wrong. I am not sure where to add the desired emblem. I use the tango theme. So would i put the emblem in "scalable/emblems/" or lets say "/32x32/emblems/" ?

-thanks
anthony

---

### Post by kerry_s on 2007-01-20
I don't know what to tell you, i can't get it to work. :(

Apparently there's a bug on that feature-> [http://thunar.xfce.org/pwiki/documentation/faq](http://thunar.xfce.org/pwiki/documentation/faq)

---

### Post by tpnerdcore on 2007-01-20
eh its ok man thanks alot though. I appriciate all of your time and efforts. I just wish either i could add a custom folder, or a laucher to an application on the side pane in thunar. Im so used to nautilus. But oh well ill figure it out. Thanks again.

-anthony

---

### Post by kerry_s on 2007-01-21
You can use a custom action(edit>configure custom actions) in the right click for what ever you want to launch. i just have 4 right now on mine, there very easy to make. Let me know if you need help with that, here's a example of my root-edit, which i use alot.

Example:
name: root-edit
command: gksu mousepad %f
filepattern: *
appears: text file, other file

---

### Post by tpnerdcore on 2007-01-21
SOLVED!

ok what i did was copied a scalable .svg icon to "/usr/share/icons/Tango/scalable/emblems/" and named it "emblem-sound.png". Then i copied the same icon to "/usr/share/icons/gnome/48x48/emblems/" and named it "emblem-sound.png". .. .. The same works for anything. i already did emblems for multimedia and sound.  and they work.

so tell me if i am unclear.

-anthony

---

