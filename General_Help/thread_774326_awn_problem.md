---
title: "awn problem"
date: 2008-04-29
forum: General Help
---

### Post by davarse on 2008-04-29
hi just install awn on my laptop (aspire 5920), and i think is wrong in here... anyway i used Gusty Gibon
i have a problem; there is nothing in the desktop, it just the wallpaper, even no panel in it, and i could find the "application", "system", etc. and it makes computer running very slow...
i followed how to on ttp://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml 
and one of the trick is to remove gnome-panel from "session", under System -> Preferences -> Sessions, and i did..
is anyone has the same experience???
how can i fix the awn??? or how can i get my gnome-panel back and set to normal desktop???
please help:(

---

### Post by scouser73 on 2008-04-29
> **davarse said:**
> hi just install awn on my laptop (aspire 5920), and i think is wrong in here... anyway i used Gusty Gibon
i have a problem; there is nothing in the desktop, it just the wallpaper, even no panel in it, and i could find the "application", "system", etc. and it makes computer running very slow...
i followed how to on ttp://news.softpedia.com/news/Create-Your-Own-Sexylicious-Ubuntu-Desktop-80189.shtml 
and one of the trick is to remove gnome-panel from "session", under System -> Preferences -> Sessions, and i did..
is anyone has the same experience???
how can i fix the awn??? or how can i get my gnome-panel back and set to normal desktop???
please help:(

I would suggest that you do a clean installation of 7.10 "Gutsy Gibbon" Install all the programs you need and get all the updates, then once this is done click Update manager for Hardy. If you have AWN installed prior to updating to Hardy, then it will work perfectly.  I know this method takes a lot of messing about, but it will work.

Visit [http://ubuntuforums.org/showthread.php?t=385981]("http://ubuntuforums.org/showthread.php?t=385981") for help installing AWN.

Hope this is of use to you.

---

### Post by crash91 on 2008-04-29
You cannot see AWN because it requires a compositing manager enabled. Go to System>Preferences>Appearance>Effects and then make sure either "Normal" or "Extra" is chosen.

To get the panel back, hit Alt+F2, then type gnome-panel. Now go to the Sessions window and click add, and in the Command box put gnome-panel.

---

