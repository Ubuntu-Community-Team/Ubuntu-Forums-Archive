---
title: "cannot delete last gnome-panel"
date: 2007-10-28
forum: General Help
---

### Post by tyler_roach on 2007-10-28
Hi

I have installed am and using Avant as a replacement for gnome-panel. I want to totally remove the gnome-panel from my desktop, but for some reason, when I right-click on the panel, the choice "delete this panel" is shaded, and I cannot choose it! is there any way to fix this, or is there another (text-based way to remove all gnome-panels from the desktop?

Thanks.

---

### Post by Seisen on 2007-10-28
You can kill gnome-panel but when you restart it will be there again, unfortunately you cannont remove the last panel but you can hide to it won't show up unless you move your mouse near it.

---

### Post by KCMOStealthRT on 2007-10-29
You can hide it more by following these steps. 

1. Run (alt +F2) "gconf-editor"
2.Go to apps/panel/toplevels/top_panel or /bottom_panel
3. change the auto_hide_size to "1" if you want it to unhide with mouse over or "0" if you don't want it to show up when you put your mouse over it.

---

### Post by LOhateVE on 2007-11-15
I found also setting the delay time to 99999 prevented it from popping back up... unless left there for extremely long ofcourse.

---

### Post by SamsLembas on 2007-12-02
I found none of the above fixes to work for me (I could still see a large amount of it even when hidden), but setting "monitor" to 3 works (I only have one monitor, but it seemed to show up anyway when set to anything lower). Obviously, you will need to increase this number if you have too many monitors.

---

### Post by AntonGr on 2007-12-04
I was looking for the same solution and just found out it myself.
The solution is throw the gconf-editor. 
You have to mark next :
 - auto-hide = yes
 - auto-hide-size = 1
 - expand = no
 - x = 10000
 - y = 10000

And you won't see any panel-pixel. Of course it isn't the right way, but among others ( clear every line about panel in gconf or deleting gnome-panel packet ) has it's merits. For example, you can trick it with other panels, then recovering them simply in gconf, all applets, icons, links of the panel will be saved.
I think the deal is in only one setting of x or y ( don't matter )  to high rate, for sure i set both.

It's not good method, to my mind gnome-developers should add smth like 'hide all panels' or make active 'remove panel' for last panel.

Best regards, Anton

---

### Post by Orkun Sensebat on 2007-12-21
way simpler would be - i think at least - to simply select "gnome-panel" under Preferences > Sessions > Current Session and change its style to trash.


hope that helps(and is way more elegant if it works)

---

### Post by OliverN on 2007-12-25
> **Orkun Sensebat said:**
> way simpler would be - i think at least - to simply select "gnome-panel" under Preferences > Sessions > Current Session and change its style to trash.


hope that helps(and is way more elegant if it works)

then couldn't you just set ''killall gnome-panel'' to fire with each session?

---

### Post by LinuxIsInnovation on 2007-12-27
I did that, but the style reverts back to "Restart" each time and the killall gnome-panel becomes ineffective

---

### Post by LinuxIsInnovation on 2007-12-27
It worked for me:
Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

This will hide the panel permanently. :grin:

---

### Post by OliverN on 2007-12-27
> **sayakb said:**
> I did that, but the style reverts back to "Restart" each time and the killall gnome-panel becomes ineffective

that used to happen for me as well.

look, I'm not calling this a fix or anything, but after doing killall gnome-panel from the terminal and seeing it reappear a couple of times, I kinda freaked out and spammed the command into the terminal in pure frustration...
guess what - it worked (?!) after 10 times or so the panel did not reappear and hasn't done since! I've now got killall-gnome-panel firing with my sessions, and I haven't seen the damn thing since.

I know it's kinda stupid - there probably could be a ton of reasons why the panel has ''given up'', but it couldn't hurt for you to try.:)

---

### Post by OliverN on 2007-12-27
''Desktop: Intel Core2 Quad Q6700 2.66GHz, 2GB DDR3 RAM, nVidia 8800 Ultra, 540GB HDD (Vista x64)
Laptop: Intel Core2 Duo T7700 2.4GHz, 2GB DDR2 RAM, Intel GMA950, 250GB HDD (Gutsy amd64 + Gnome)''


holy crap, dude...

---

### Post by LinuxIsInnovation on 2007-12-29
My desktop is shared by me and my 5 brothers with all our income :D
And.. the laptop aint too costly ;)

Btw, I did something new. I deleted the panel and saved my session. So whenever I log on, It restores the session and the panel isnt loaded :D

---

