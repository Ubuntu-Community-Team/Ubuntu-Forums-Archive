---
title: "Is there a gui task script maker for ubuntu?"
date: 2008-04-19
forum: General Help
---

### Post by computergroove on 2008-04-19
I have used Autoit for making incredible scripts in Windows but I cant seem to find a gui script maker for linux. I have found info on bash and shell scripts but I want the ability to:

If (768,345) = blue
      left click x coordinate 768, y coordinate 345. 
      Wait 3 seconds. 
      Type "123" hit enter." 
else
      type "f5"

Can bash do this? Is there a program that does? I want to make a script and roll it up into a live cd that loads it on startup.

---

### Post by ryanhaigh on 2008-04-19
A quick search in synaptic package manager (System>Administration>Synaptic) finds these things which may be useful. 

xnee - X event recorder/replayer
xmacro - Record / Play keystrokes and mouse movements in X displays
xautomation - Control X from the command line, and find things on the screen

I have personally used xautomations xte app for some simple keyboard scripting with bash
```

#Bash script to simulate keyboard input (use keydown && keyup for key combos)
#eg fdupes --delete
counter=100
limit=0
sleep 3s &&
 while [ "$counter" -gt "$limit" ];
do
xte "key 1" &&
xte "key Return";
done

```

Reading the man pages for those apps should give you everything you need for some scripting. For livecd you may want to keep in mind that the systems may boot with different resolutions and with different speeds. xautomation may be good in that it will let you search for things on the screen (so you know that your app has opened for instance) but you may also want to look at wmctrl which will allow you to manipulate the positions of windows. Finally just incase you do not know, in order to have these run from startup you should make a new item for the script in System>Preferences>Sessions for the livecd and remember to use the full paths to the applications (although I have never personally had an issue with this as you can see in my script, others have).

EDIT: You can also use wmctrl to ensure that the window you are targetting is currently active.

---

### Post by SPr on 2008-04-19
Is there anything in this discussion > [www.usenet-forums.com/linux-general/84599-sendkeys-equivalent-linux.html](www.usenet-forums.com/linux-general/84599-sendkeys-equivalent-linux.html) that helps?

---

