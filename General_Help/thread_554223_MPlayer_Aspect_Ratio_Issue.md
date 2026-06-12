---
title: "MPlayer Aspect Ratio Issue"
date: 2007-09-18
forum: General Help
---

### Post by taekwondodogoof on 2007-09-18
Hi,
     I have a 1680x1050 monitor. Just recently, when I play a movie in MPlayer, it stretches to the width of my screen, but not the height. I can manually change it by dragging the sides, but changing the aspect ratio from the menu doesn't fix it. Also, when I add monitor aspect 16:10, mplayer won't boot, and doesn't give me an error. When I remove that option, it boots fine. Does anybody have any ideas? 
               Thanks for the help!

---

### Post by taekwondodogoof on 2007-09-19
Bump!

---

### Post by size_XXM on 2007-10-23
I have the exact same problem! :( Sadly, I don't know how to fix this but strangely, other Mplayers front-ends (such as SMplayer, KMplayer...) don't have this problem (yes, I use Kubuntu - you'll probably be better off with some Gnome/GTK-based GUI for MPlayer).

---

### Post by rvm4000 on 2007-10-23
For old versions of mplayer, I think it's needed to use -monitorpixelaspect 1 for non 4:3 screens.

---

### Post by oobuntoo on 2007-10-24
1. sudo kate /etc/mplayer/mplayer.conf 
 
    (or sudo gedit /etc/mplayer/mplayer.conf  for gnome user)
 
2. Uncomment the line "# monitoraspect = 16:9"; that is remove "#"

3. replace 16:9 with 1.6

4. Save and restart mplayer

---

### Post by size_XXM on 2007-10-25
Thanx, monitoraspect=*x: x* worked. BTW, monitors are 16:10, only TVs are 16:9 ;)

---

