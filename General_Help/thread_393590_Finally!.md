---
title: "Finally!"
date: 2007-03-25
forum: General Help
---

### Post by rgmaxey on 2007-03-25
Well, it took a couple of weeks of struggling, but I finally figured out wireless and now have a fully functional Linux system. I'm really enjoying it. Not saying I'm ready to ditch Windows and Mac (I have all three), but I like Linux and am glad I've added it to the mix. 

Just three minor points left to address (OK, I lied a little when I said it was fully functional, but these are problems I can live with if I have to):

1. How do I get gdesklets (I think that's what the widget application is called) to load on startup? I'm sure it's a matter of adding a line to some file, but I have no idea what it is.

2. Why can't I get video in Realplayer 10? It seems to have installed properly, but there's no video. I suspect that's why I can't get video on some websites, such as Fox News, where there's audio but no picture, just a black screen. (CNN, which uses mplayer, works fine.)

3. Does anybody know if there's a solution to the shutdown/reboot problem with the GUI? If I shut down from the command line, it works everytime. However, if I click the restart or shutdown buttons on the menu, it works correctly maybe 50 percent of the time; the rest of the time it just crashes upon leaving the desktop and I have to turn off manually by holding down the power button for a few seconds, which I'm sure isn't a good thing to do.

---

### Post by Nikron on 2007-03-25
1.  For gnome, you add Gdesklets under System --> Preferences --> Sessions.  However I'd recommended not using gdesklets considering they were not actively developed for a while, and are only recently regaining activity.  Look into superkarmba or adesklets.  
2.  You have to install plugins for mozilla.  I"ll go look for a guide and post back here if I find the one I followed.  I'm pretty sure there isn't a realplayer plugin for fire fox., but who knows..

3.  I have no idea why that's happening.  You might want to look in your /var/log/syslog at the time of shutdown/reboot

---

### Post by sdowney717 on 2007-03-28
for fox news you can use a grease monkey script. Search for it and you will be able to watch video. I had same problem

---

### Post by sdowney717 on 2007-03-28
[http://vlajbert.blogspot.com/](http://vlajbert.blogspot.com/)

here it is. I just checked it and it is working fine.

---

