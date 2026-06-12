---
title: "Create a custom system message,is it doable?"
date: 2013-02-18
forum: General Help
---

### Post by cogset on 2013-02-18
Hi there,I was thinking if there's any way to create a custom-made  system message (notification),like say the one popping up when the  network goes up or down.
I was going to add a cronjob  to  rsync some directories on an external drive every day,only that drive  won't be plugged in all the time,so a pop up message saying something  like "cronjob starting in 5 minutes,plug in the drive" would be kinda  handy ;)
Can this be done in Gnome 2 ?

---

### Post by scbingham on 2013-02-18
motd (Message Of The Day) will display the contents of file /etc/motd when users log in.

wall (Warn ALL) will display the contents of a file to all logged in users. You could put this at the beginning of your script.

I used these commands in the pre GUI days of unix, so I'm sure there are prettier ways of doing something similar now.

---

### Post by Lars Noodén on 2013-02-18
Would [zenity](http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html) be of use?  It provides a graphical popup.

```

DISPLAY=:.0. zenity --notification --text 'Hello, World'

```

---

### Post by sudodus on 2013-02-18
See this thread which uses notify-send

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2115215[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2115215")

---

### Post by cogset on 2013-02-18
> **Lars Noodén said:**
> Would [zenity]("http://manpages.ubuntu.com/manpages/precise/en/man1/zenity.1.html") be of use?  It provides a graphical popup.

```

DISPLAY=:.0. zenity --notification --text 'Hello, World'

```

Oddly,zenity delivers only a tiny tooltip in the notification area (to see which you have to hover on the icon that pops up there) in Lucid with Gnome 2,but a nice full-sized notification balloon in Debian with Mate desktop.
From what I've read,looks like some people had such issues with zenity - maybe some extra libraries/packages are needed to have this notifications properly displayed?

EDIT: OTOH,after installing libnotify-bin as suggested in the next  reply, and using notify-send,the notifications apparently work straight  away from the command line.
Having them appear by means of a cronjob took more work,however:I ended up  crafting a simple script like this 
> #!/bin/sh
/usr/bin/notify-send 'rsync cronjob starting IN 5 MINUTES :
PLUG IN USB Device ! ' and then adding this cronjob

> DISPLAY=:0 
30 08 * * * /home/user/scriptfollowing the directions in this article [http://www.guyrutenberg.com/2012/08/17/sending-desktop-notification-from-cron/](http://www.guyrutenberg.com/2012/08/17/sending-desktop-notification-from-cron/) -actually,many suggestions about how integrating messages with a crontab were too complicated for what I needed,this simple script (well just a cut and paste job,really ;) ) does what I need.
Thanks for all the hints,BTW ;)

---

### Post by Habitual on 2013-02-18
```
notify-send -t 10000 -u critical "cronjob starting in 5 minutes, plug in the drive"
```

---

