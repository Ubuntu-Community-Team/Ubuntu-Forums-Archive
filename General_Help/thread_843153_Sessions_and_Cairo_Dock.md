---
title: "Sessions and Cairo Dock"
date: 2008-06-28
forum: General Help
---

### Post by jason50146 on 2008-06-28
Hi-

I'm having trouble adding cairo-dock to my sessions list.  

I have cairo-dock configured and running fine, but I can only start it from the system tools menu.

When I add cairo-dock to my sessions list and reboot, cairo-dock does not start.  Then, when I check the sessions list, cairo-dock is not there, even though I added it before the reboot.  I double checked and "cairo-dock" is the correct command to start it up.

I have not tried adding other programs to my session list, so I'm not sure if there is a larger issue here.  Anybody seen this behavior before or have any suggestions?  I'm running Hardy with Cairo Dock 1.6.0.2

Thanks!

-----
Remember when computing was fun?  C=64, Amiga

---

### Post by Forlong on 2008-06-29
I guess Cairo-Dock depends on Compiz -- so if Compiz is not yet loaded when cairo-dock is issued, it won't work.

Try setting up a small script to work around this:
Run
```
gedit ~/start-cairo
```
Paste this in there:
```
#!/bin/bash
sleep 15
cairo-dock &
```
And save.

Then make it executable:
```
chmod +x ~/start-cairo
```

Finally, go to your Startup Programs and use this script instead of the cairo-dock command there (you can find it in your home directory).

Hope it helps.

---

### Post by fabounet on 2008-06-30
I don't have a solution for you, but CD runs without Compiz, and you can perfectly start Compiz after the dock.

does "which cairo-dock" in a terminal gives you something like /usr/bin ?
did you type it correctly in the session manager ?

---

### Post by jason50146 on 2008-07-02
> **fabounet said:**
> I don't have a solution for you, but CD runs without Compiz, and you can perfectly start Compiz after the dock.

does "which cairo-dock" in a terminal gives you something like /usr/bin ?
did you type it correctly in the session manager ?

I checked and the full path was /usr/bin/cairo-dock.  I tried that in sessions and still no joy.

---

