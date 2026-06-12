---
title: "Sudo Killall xorg didn't work :S"
date: 2007-07-07
forum: General Help
---

### Post by zanazzi on 2007-07-07
While attempting to get gfx card drivers installed i came across the problem highlighted in the title.

I managed to get around it simply by commenting out a line.

Does anyone have any idea why killall xorg didn't work?

---

### Post by johnsd8 on 2007-07-07
you should probably be using
[FONT="Courier New"]/etc/init.d/gdm stop[/FONT]

instead, assuming you want to shutdown X to install a new driver.

I bet kill -9 would work however, but X would likely immediately restart

---

### Post by zanazzi on 2007-07-07
i actully tried: sudo killall gdm; sudo killall xorg

it didn't work so corrupted the file with a comment, i was wondering why the killall command didn't work for xorg?

[edit] i wasn't running a gui at the time was in alt+ctrl+F2

---

