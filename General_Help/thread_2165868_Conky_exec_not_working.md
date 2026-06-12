---
title: "Conky exec not working"
date: 2013-08-06
forum: General Help
---

### Post by BitJunkie on 2013-08-06
I'm trying to use exec in conky to display the battery capacity from a connected android device. Here is the line:
```
${if_running adb}Android: ${exec adb shell cat /sys/class/power_supply/battery/capacity | tr -d [:cntrl:]}% $endif
```
with the result
```
Android: %
```
If I open a terminal, kill conky and restart it, it works fine. The only difference I can see is that when conky autostarts, it isn't associated with any terminal, whereas after I restart it from a terminal it is associated with that terminal. 

I've tried putting the adb stuff in a shell script that writes to a file but after the exec the file only contains a 0x0a. The script worked fine from a command line. I've tried the variations of exec (execi, texeci, etc.) but none of those work either.

The conky update interval is 3 seconds. Any ideas?

---

### Post by deadflowr on 2013-08-06
Are you trying to get it to work at startup?
If so, try setting a delay for conky.
```
conky -p 20
```
With conky being conky, -p means pause before launching conky and 20 meaning 20 seconds to delay launching conky.
I fine adding a delay to launch conky usually lets all the little things the system does get done and conky runs fine after.
You can adjust the time if you want.
And if you run a specific conky file that is not .conkyrc, then
```
conky -c file -p 20
```

---

### Post by BitJunkie on 2013-08-06
Yes I am running conky at startup. I am running it from a script that sleeps 25 seconds before running conky. Maybe I'll try the -p switch instead and see if it makes any difference.

---

### Post by Habitual on 2013-08-06
Try this:
```
${if_running adb}Android: ${execpi 600** [COLOR=#ff0000]/path/to/adb[/COLOR]** shell cat /sys/class/power_supply/battery/capacity | tr -d [:cntrl:]}% $endif
```

Nice job too on that routine, it's "Shiny". ;)

Also:
```
 conky -v | head -1
``` too please.

---

### Post by BitJunkie on 2013-08-06
Thanks, Habitual! Adding the path to adb worked. I figured I was missing something simple like this. 

And for completeness, and as requested,
```
$ conky -v | head -1
Conky 1.8.1 compiled Fri Dec 16 18:29:36 UTC 2011 for Linux 2.6.24-30-server (x86_64)

```

Thanks again!

---

### Post by Habitual on 2013-08-06
Good Job
Want something else to work on? Check [this]("http://s771.photobucket.com/user/E522260/media/desktop_9_21_2010.png.html")
I still have all the code, 'tho' I don't run but one "widget" these days.

Enjoy!

---

### Post by BitJunkie on 2013-08-06
Yikes! I would like to see the code, but I don't think I would ever attempt something like this. Conky and I have a fragile relationship and I think this would make me pull (the rest of) my hair out. :)

---

### Post by Habitual on 2013-08-07
(conky) coding is a drug. And I am Habitual in most things. ;)
If you understand and can assemble 
```
 ${if_running adb}Android: ${execpi 600** [COLOR=#ff0000]/path/to/adb[/COLOR]** shell cat /sys/class/power_supply/battery/capacity | tr -d [:cntrl:]}% $endif
```
you'd have few issues.

Good Luck! and have fun.

---

