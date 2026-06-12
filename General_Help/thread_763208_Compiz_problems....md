---
title: "Compiz problems..."
date: 2008-04-22
forum: General Help
---

### Post by MaverickHunter on 2008-04-22
If I have Compiz running and try to run a full screen application; the screen flashes a bit, and if I disable compiz completely before running the application, it doesnt do this.

So my question is if there is a way to automatically have compiz disable itself when I run an application in full screen, and re-enable it when I close the application?

Thanks for any help!

---

### Post by irunwithknives on 2008-04-22
im not sure how to do what you asked, but what window effects and such do you have enabled?

---

### Post by russo.mic on 2008-04-23
And also, what applications cause the flashing?  

Compiz takes a miniute to startup up and shut down, so you'd just end up having to wait longer for the app.  Besides, as you started/shut it down, you'd have a flash.

That seems like a problem that can be fixed, depending on what it is your doing.  Why don't you try and be a bit more descriptive?

Russo

---

### Post by Crafty Kisses on 2008-04-23
> **MaverickHunter said:**
> If I have Compiz running and try to run a full screen application; the screen flashes a bit, and if I disable compiz completely before running the application, it doesnt do this.

So my question is if there is a way to automatically have compiz disable itself when I run an application in full screen, and re-enable it when I close the application?

Thanks for any help!
You might be able to make a script, but I'm not sure. This issue could probably be resolved if we had a little bit more information.

---

### Post by MaverickHunter on 2008-04-23
> **russo.mic said:**
> And also, what applications cause the flashing?  

Compiz takes a miniute to startup up and shut down, so you'd just end up having to wait longer for the app.  Besides, as you started/shut it down, you'd have a flash.

That seems like a problem that can be fixed, depending on what it is your doing.  Why don't you try and be a bit more descriptive?

Russo

Its any application thats runs in full screen. I guess to be more descriptive, where my task bar would be flashes back and back to the proper colour of the full screen app, or sometimes in the middle of the screen.

It seems to be kinda random in terms of what flashes and such.

Also, as for the effects, I have pretty much all of the availible ones installed and running :/

I was thinking it could be like Vista, where as soon as you launch a full screen app Aero disables itself.

---

### Post by Cresho on 2008-04-23
Simple stuff!

rightclick on the desktop and create document and empty file.  Now rename it to yourapplicationname.sh then you right click on it ahd allow as executable.  paste this next part in it

```
#!/bin/bash
#Script Compiz/on/off

# Compiz off;
killall compiz.real &
metacity --replace &

#run game;
cd /home/yourusername/Installed_Programs/Typhoon_2001
./typhoon

#Compiz on;
compiz --replace &
```

if you are running emerald, then you the last part should say "emerald --replace &" after the compiz portion

you can right click on the application and edit menu and navigate to your executable and change the command to directed to this file.  and when you click on it, it will perform this task and after you are done,

---

