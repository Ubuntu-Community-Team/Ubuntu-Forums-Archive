---
title: "Delaying startup applications in 14.04"
date: 2014-06-29
forum: General Help
---

### Post by newb85 on 2014-06-29
So, I've seen several tutorials around the web with the same instructions, saying they work on recent releases, including 14.04.  The instructions are simple: open Startup Applications and prefix the startup commands with sleep commands.  Eg:

```
sleep 30; dropbox start -i
```

I tried it head-first with several applications.  The boot-up process was indeed faster.  The only problem is, the applications didn't start at all.  This was observed not only with dropbox, but also with indicator-multiload, my-weather-indicator, and variety.

The approach makes perfect sense, so why isn't it working?

Thanks!

---

### Post by Bucky Ball on 2014-06-29
*Thread moved to **General Help**.*

---

### Post by Frogs Hair on 2014-06-29
I have started such scripts with the following for desktop applications.```
#!/bin/bash 
sleep 10 && application name; 
```

Create a text doc with gedit, save in a folder, make it executable in properties and add to startup applications navigating to the script from startup applications.

---

### Post by newb85 on 2014-06-29
That makes sense.  But I shouldn't have to create the script.  Entering the command directly into the Startup Applications command line *should* work.

---

### Post by Bucky Ball on 2014-06-29
Yep, so edit or create your startup entry and try:

sleep 10 && dropbox

You may also need the ';' at the end, not sure, and not sure if this will work, but Frogs Hair can probably confirm. ;)

---

### Post by mc4man on 2014-06-29
In general you just need to add a line to the .desktop associated to your startup app or command, where blue X is number of seconds. - 
X-GNOME-Autostart-Delay=[COLOR="#0000CD"]X[/COLOR]

In the case of dropbox it seems to rewrite it's startup .desktop each time so here I do this

In Dropbox > Preferences disable the "Start Dropbox ..." option

Then 
```
gedit ~/.config/autostart/dropbox1.desktop
```

Use something like this, adjust seconds to suit
```
[Desktop Entry]
Type=Application
Name=Dropbox
GenericName=File Synchronizer
Comment=Sync your files across computers and to the web
Exec=dropbox start -i
Icon=dropbox
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=30
```

save & see...

---

### Post by philinux on 2014-06-29
Alternatively this does works for me in startup apps.

```
bash -c "sleep 20 && conky"
```

---

### Post by newb85 on 2014-06-29
@Buckyball, Yeah, I had tried that.  Regardless of whether I used the ending ";", that didn't work, either.

@mc4man and @philinux, Those probably work (I haven't yet tried them), but they're more involved than this should be.  I shouldn't *have* to edit .desktop files to delay startup processes.  Also, I shouldn't have to tell Startup Applications to use bash.  When I try running the command from the terminal (using the default sh shell), the sleep commands are carried out just fine.  The bottom line is that something isn't working the way it is designed to (or at least appears to be designed to) work.

As a step toward troubleshooting, the issue isn't in transitioning from the sleep command to the app command.  Running 
```
ps -e | grep sleep
``` during the sleep time window doesn't yield anything.  In other words, the sleep command isn't even executing.

---

### Post by mc4man on 2014-06-29
> **newb85 said:**
> @Buckyball, Yeah, I had tried that.  Regardless of whether I used the ending ";", that didn't work, either.

@mc4man and @philinux, Those probably work (I haven't yet tried them), but they're more involved than this should be.  I shouldn't *have* to edit .desktop files to delay startup processes.  Also, I shouldn't have to tell Startup Applications to use bash.  When I try running the command from the terminal (using the default sh shell), the sleep commands are carried out just fine.  The bottom line is that something isn't working the way it is designed to (or at least appears to be designed to) work.

As a step toward troubleshooting, the issue isn't in transitioning from the sleep command to the app command.  Running 
```
ps -e | grep sleep
``` during the sleep time window doesn't yield anything.  In other words, the sleep command isn't even executing.

I would disagree - 
Startup applications uses & or creates .desktop files & places them in ~/.config/autostart/ 
(as does dropbox when it's set to autostart in it's preferences.

So the "working the way it is designed to " in this regard is fine. If a user wants to delay then because startup applications presents no such option the adding of the appropriate line to the .desktop is the correct manner

In most cases one wouldn't need to create a new .desktop, at least here dropbox is the exception.

If you wish to do via the Exec= of the startup .desktop then create an executable script in your PATH & then set your autostarts's command to the name of your script

---

### Post by newb85 on 2014-06-29
All right, mc4man, your prodding has convinced me to give your approach a try.  However, I still maintain that adding the sleep command directly to the Startup Applications GUI *should* work.  The fact that it *used to* work seems to back that up.

---

### Post by grumblebum2 on 2014-06-29
> **newb85 said:**
> All right, mc4man, your prodding has convinced me to give your approach a try.  However, I still maintain that adding the sleep command directly to the Startup Applications GUI *should* work.  The fact that it *used to* work seems to back that up.
Pretty sure I have always had to use 
```
sh -c "sleep xx && [COLOR="#808080"]<application>[/COLOR]"
```
or use the path to a script in startup applications.

---

### Post by mc4man on 2014-06-29
> **newb85 said:**
> All right, mc4man, your prodding has convinced me to give your approach a try.  However, I still maintain that adding the sleep command directly to the Startup Applications GUI *should* work.  The fact that it *used to* work seems to back that up.
Well,  the point I was trying to make is this - 
When you create or edit the command line in Startup Applications,  whatever used is what will go on the Exec= line in that .desktop
So if you can fashion a command that works on an Exec= line in a .desktop, fine.

In this case, delaying the start up time,  there is already a .desktop line available -,   X-GNOME-Autostart-Delay=
So why not just use it...

(- the unusual thing here was just with dropbox, if I added the line to it's .desktop it would work but then the line would disappear. never seen that before
So creating a new .desktop with different name seemed easiest to figuring out why it was being removed. In all other times I've just added the line if not already there.

---

### Post by newb85 on 2014-06-30
You're correct.  And the method you suggested worked like a charm (once I had the spelling correct and removed the trailing ";" from the Exec= line that I had added earlier).

Part of my problem is that I'm thinking of new Ubuntu users.  Some of them will search for ways to speed it up, and inevitably come across one of the several tutorials that start with delaying startup applications.  (The ones I've come across all follow the method mentioned in my original post.)  They'll try it.  It won't work.  Their view of Ubuntu will be slightly tainted.

And part of my problem is that this is but one of a laundry list of instances I've found where one can read about something cool you can do, only now you can't do it that way anymore because someone decided to do away with that functionality, or there's a bug they're denying is a bug, or there's a bug they fixed but only released the fix for the beta release of Ubuntu, etc, etc, etc.  [end rant]

---

### Post by Rod J on 2015-02-04
> **mc4man said:**
> ... (- the unusual thing here was just with dropbox, if I added the line to it's .desktop it would work but then the line would disappear. never seen that before
So creating a new .desktop with different name seemed easiest to figuring out why it was being removed. In all other times I've just added the line if not already there.

I've been having trouble with Dropbox on my new install just lately (Kubuntu 14.04, Dropbox 3.0.5). Dropbox keeps resetting the delay I want before it starts (I'm using a Wifi hotspot for my internet and have to log in before the internet is available. If Dropbox tries to access the internet before I log in it keeps giving an error complaining about wrong time zone or other nonsense). 

My solution was to simply make my modified dropbox.desktop file read only and that stopped the Dropbox paranoia.

---

