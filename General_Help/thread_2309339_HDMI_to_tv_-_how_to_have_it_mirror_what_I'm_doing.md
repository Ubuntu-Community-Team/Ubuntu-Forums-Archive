---
title: "HDMI to tv - how to have it mirror what I'm doing?"
date: 2016-01-09
forum: General Help
---

### Post by michael-piziak on 2016-01-09
HDMI to tv - how to have it mirror what I'm doing?

It's just showing my desktop background on screen

---

### Post by QDR06VV9 on 2016-01-09
> **michael-piziak said:**
> HDMI to tv - how to have it mirror what I'm doing?

It's just showing my desktop background on screen
Hi michael-piziak see if the site below gets you sorted out.
[http://askubuntu.com/questions/518700/laptop-tv-sync-problems-in-ubuntu-14-04](http://askubuntu.com/questions/518700/laptop-tv-sync-problems-in-ubuntu-14-04)
Kind Regards

---

### Post by jim_deadlock on 2016-01-11
Step 1: find out the ID of your TV:

```
xrandr
```

In my case, my TV is HDMI-0

Step 2: open "Startup Applications" and add a new item with this as the command (replace HDMI-0 with your ID):

```
xrandr --output HDMI-0 --pos 0x0
```

Step 3: reboot and hopefully your screens will be the same.

---

### Post by michael-piziak on 2016-01-11
Thanks all, I got it to work with all your help.

One other quesetion:

My computer squeezes down like it's in a black box on each side but my tv monitor has the entire screen.   I would rather it be the other way around as I am playing youtube karoke with friends which will fit even if squeezed down on tv, but I want to multitask on the computer and I don't like this notebooks 17" screen squeezed down more.

Any suggestions?

---

### Post by jim_deadlock on 2016-01-11
If you do xrandr again you'll probably see the wrong screen set as the primary. You can change this in either your nVidia control panel or else Ubuntu Settings > Screen Display (or Monitors, depending on your Ubuntu version). Or just play around with your screen resolution till it looks right.

---

