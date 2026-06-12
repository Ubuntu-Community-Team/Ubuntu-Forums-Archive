---
title: "my gnome screensaver no longer launches"
date: 2007-11-23
forum: General Help
---

### Post by kraymore on 2007-11-23
my gnome screensaver no longer launches when its time.  i wish i could post some logs of some fail to help troubleshoot but i dont know where to begin.  

ps aux | grep screensaver

gives this output

avis      5716  0.0  0.0  16568  2864 ?        Ss   13:07   0:03 gnome-screensaver

it wont however switch to the screensaver after 10 minutes 

would appreciate some help

thank you

---

### Post by tormod on 2008-01-10
Does
 sleep 2; gnome-screensaver-command --activate
make it start?

---

