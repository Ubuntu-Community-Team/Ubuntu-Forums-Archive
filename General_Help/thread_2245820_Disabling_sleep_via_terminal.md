---
title: "Disabling sleep via terminal ?"
date: 2014-09-26
forum: General Help
---

### Post by jhay2 on 2014-09-26
hi is there a way to disable the monitor sleep using terminal command ?


i did this ,
[http://www.tech-recipes.com/rx/2791/ubuntu_stop_display_sleep_when_inactive/](http://www.tech-recipes.com/rx/2791/ubuntu_stop_display_sleep_when_inactive/)

but no effect it still sleep 
i need to disable this not for my laptop but on my friend's laptop , 
when the monitor sleeps and decide to login the account again after login the graphics messed out, lines appeared all over the monitor screen and i cant see anything except those lines. -_-  i dont know what to do with this problem 


so if someone here knows how to disable the monitor sleep or a suggestion  to fix the graphics issue after monitor sleep 

please help 

thank you

---

### Post by Dennis N on 2014-09-26
Restricting the options to using a terminal command, **xset -dpms** may work. See xset man page for all details - (in terminal, **man xset**). 

A similar post to study: [http://ubuntuforums.org/showthread.php?t=2245139](http://ubuntuforums.org/showthread.php?t=2245139) In Lubuntu, you have light locker instead of gnome screensaver.

---

