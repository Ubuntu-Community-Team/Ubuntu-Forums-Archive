---
title: "[SOLVED] Nice/ Smooth Login"
date: 2008-05-21
forum: General Help
---

### Post by Ohwii on 2008-05-21
Hi Guys,

is it possible to smoothen the login in ubuntu. every time I start ubuntu the awn icons float into the bar, there are fragments loading and the desktop turns black for a short time. 

Well I use compiz.( just as a info ) 

It would be very nice if someone could help.Thanks 

oh wii

---

### Post by Forlong on 2008-05-21
Write yourself a script to load everything with a short delay.

Like this:
```
#!/bin/bash
sleep 5
compiz &
while [ -z $(ps -o comm= -C compiz.real) ]; do
  sleep 2
done
avant-window-navigator &
```

---

### Post by Ohwii on 2008-05-21
wouldnt that mean that everything loads twice. 

since I but it into the sessions manager. 

could you also write how to implement it I mean how do I auto run the scrpit

---

### Post by Forlong on 2008-05-21
You have to remove AWN's separate entry from the autostarted programs of course.
And choose *None* under *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*

---

### Post by Ohwii on 2008-05-21
Ive written the script and browsed to the file in the sessions manager. 

```
#!/bin/bash
sleep 5
compiz &
while [ -z $(ps -o comm= -C compiz.real) ]; do
  sleep 2
done
avant-window-navigator &

sleep 2 cairo-clock & 

```

but it doesnt work? 

I mean how can I let it auto run

---

### Post by Forlong on 2008-05-21
First of all
```
sleep 2 cairo-clock &
``` won't work this way.
But there's no need to delay anything further after Compiz anyway.

Try this:
```
#!/bin/bash
sleep 5
compiz &
while [ -z $(ps -o comm= -C compiz.real) ]; do
  sleep 2
done
avant-window-navigator &
cairo-clock &
```
Then save it e.g. as 'compiz-start' in your home directory.
Afterwards you have to make it executable:
```
chmod u+x compiz-start
```
Then test it:
```
./compiz-start
```
Finally let GNOME run the script on startup.

---

### Post by Ohwii on 2008-05-21
Works nice, but still the Awn creates fragments of white bars and the cairo clock is also only fragmented. :( 

The good part is that the icons are not flying anymore. =D>

thank a lot for your time. If you have some other solution to the smoothening please let me know.

bye 

oh wii

---

### Post by Forlong on 2008-05-21
I'm sorry, I am using neither AWN nor Cairo-Clock, so I can't say much about them.

Btw: if you like Cairo-Clock, you might want to try Screenlets.

---

