---
title: "No Unity bar on the left after upgrade to 12.10 - Completely Broken Desktop"
date: 2012-10-21
forum: General Help
---

### Post by montonero on 2012-10-21
Hi,
I've just upgraded Ubuntu to 12.10, rebooted it.
First it showed a message asking me to restart Nautilus, to which I replied "yes". But now I am presented with a desktop, but no Unity bar on the left.
I can't launch any applications. Although, if I double click files that are on the desktop they would open, but would not have a top bar (with minimise, maximise buttons).
Basically, new Ubuntu is completely unusable for me, and I'm typing this from a Windows machine.

Is this a known "feature" of new Ubuntu?

---

### Post by montonero on 2012-10-21
Does anyone know how is it possible to start a terminal in this scenario? There is no terminal app shortcut on desktop.

---

### Post by montonero on 2012-10-21
Ok, managed to start terminal with Ctrl-Alt-T.
But when I try to launch Unity from it, there are a number of errors related to "compiz".

---

### Post by neoroses on 2012-10-21
Hi bud i had the exact same problem, i basically had to intall gnome, by getting a terminal up with ctrl+alt+f1 and installing gnome-shall and gnome session. the ppa is [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) 

it think after adding that with 

```
sudo add-apt-repository http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu

sudo apt-get update

sudo apt-get install gnome-shell gnome-session 
```

i may have got the code slightly wrong, sorry but i think thats correct. Its not unity but it will give you a working desktop with good old gnome!

---

### Post by alphacrucis2 on 2012-10-21
I don't suppose you had autohide of the unity bar enabled? If you are using nvidia graphics, install the "experimental" driver. That will fix the autohide problem.

See this:

[https://bugs.launchpad.net/unity/+bug/1057000](https://bugs.launchpad.net/unity/+bug/1057000)

As it says there is also a workaround to add 


Option "ConstrainCursor" "no"

to the Device Section of xorg.conf.

The so called "experminental" driver is a better solution as it appears to be faster and more stable. It may vary depending on particular nvidia card.

---

### Post by kwanylongy on 2012-10-21
I am having the same issue.... 
thanks for making this post earlier than I did!

---

### Post by kwanylongy on 2012-10-21
BTW, if you still wanna make your Ubuntu machine usable for the moment, log out (Ctrl+Shift+Del), then log in with "GNOME (Classic, No Effect) - which is what I am doing at the moment.

I am really disappointed with Ubuntu's recent upgrades, since the introduction of Unity the upgrades have been really really buggy....

---

