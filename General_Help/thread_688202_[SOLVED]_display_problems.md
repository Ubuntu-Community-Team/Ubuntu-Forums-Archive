---
title: "[SOLVED] display problems"
date: 2008-02-05
forum: General Help
---

### Post by capel on 2008-02-05
I'm running 7.10 Gutsy on newish celetron D computer. yesterday when I switched on the desplay was squashed up into a small box at the top of the screen, with the task bar replicated at the bottom.

I've tried booting from the CD and everything is fine, and I've plugged the monitor into another PC and that works fine as well.

Does anyone have any ideas? or do I need to re-install?

---

### Post by stooshbunutu on 2008-02-05
It could be that the resolution is incorrect for that monitor. Under the system menu on preferences there is an option called Screen Resolution. Simply select different ones of these untill you find one that works for you.

Hope this helps :)

---

### Post by capel on 2008-02-05
Thanks, but that's not it.

The screen is split in two, with the top half of the sreen showing the screen view squashed into it with the task bar at the bottom. then there is half a screen of blank olive green with another task bar at the bottom of that.
I can only move the mouse over the top half.

All applications seem to work fine, but very difficult to read!

Help!

---

### Post by kesman on 2008-02-05
Open up another tty by pressing ctrl+alt+f2 or some other f-key. Then login as your username. Then shutdown your gdm with
```

sudo /etc/init.d/gdm stop

```

and then make a backup of your xorg.conf with
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
then reconfigure your xorg settings with
```

sudo dpkg-reconfigure xserver-xorg

```
and be extra careful when you pick up resolutions and monitor sync rates. You can find the supported refersh rates in the monitor manual or manufacturer's website.
then restart your xorg with
```

sudo /etc/init.d/gdm start

```

Good luck!

---

### Post by capel on 2008-02-05
Hi, I've tried that, but I'm getting message ....missing destination file operand after '/etc/Xll/xorg.conf.backup'

Any ideas?

Capel

---

### Post by kesman on 2008-02-05
it's X11, not XII or Xll or X||. X-eleven.

---

### Post by kesman on 2008-02-05
from now on, use TAB key to complete words in terminal. I mean, first type /et, and then press TAB. Then type X and press TAB. If nothing happens, press TAB again and it gives you list of files or directories that start with X.

---

### Post by capel on 2008-02-05
Thanks Kesman,
But I'm still getting the same message. missing destination file operand after '/etc/X11/xorg.conf.backup
Any other ideas? 
Capel

---

### Post by Zwack on 2008-02-05
> **capel said:**
> Thanks Kesman,
But I'm still getting the same message. missing destination file operand after '/etc/X11/xorg.conf.backup
Any other ideas? 
Capel

Post the results of 
ls -l /etc/X11

I'm curious... It sounds like it doesn't think that you are giving it the right number of parameters.

sudo  cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup

is two commands (sudo and cp) and two parameters (the two file names)...  It almost sounds like you missed one of the file names, like this...

```

$ sudo cp /etc/X11/xorg.conf
cp: missing destination file operand after `/etc/X11/xorg.conf'
Try `cp --help' for more information.
$ 

```

Z.

---

### Post by capel on 2008-02-05
That's exactly what I'm seeing on my screen but I'm definately putting in just what you tell me......strange.

Capel

---

### Post by capel on 2008-02-05
Sorry, I've just reallised that the last message was from Zwack...woops.
The plot thickens, I've rebooted the computer and now it is only showing an olive screen with some dots all over it. by moving the mouse I can see more or less where it is going, but nothing else.???

---

### Post by kesman on 2008-02-06
So you did dpkg-reconfigure xserver-xorg? If this doesn't work, you must've selected something wrong. Try again and when it asks for your monitor specs, select "simple" method.

---

### Post by capel on 2008-02-06
Kesman, you're a star.

Thank you very much, everything is back to normal.

I ran through the whole thing again and I guess I must have made a mistake at some point.

Thanks again.

Capel

---

### Post by kesman on 2008-02-06
Maybe mark this thread as "solved" then?

---

### Post by capel on 2008-02-06
now marked as solved, sorry I'm new to this.

Thanks again

Capel

---

