---
title: "Getting an Emerald theme to stay?"
date: 2008-04-19
forum: General Help
---

### Post by LasseNC on 2008-04-19
Simple I hope! 

When I close terminal, my Emerald themes disappear, added the "emerald --replace" to sessions, but nothing yet, any ideas? 

Kind regards!

---

### Post by overdrank on 2008-04-19
> **LasseNC said:**
> Simple I hope! 

When I close terminal, my Emerald themes disappear, added the "emerald --replace" to sessions, but nothing yet, any ideas? 

Kind regards!

Hi and you can try the alt, F2 keys and then use ```
emerald --replace
```.

---

### Post by LasseNC on 2008-04-19
> **overdrank said:**
> Hi and you can try the alt, F2 keys and then use ```
emerald --replace
```.

Am I supposed to run that everytime I start up?

When I right click on my desktop and navigate to the fan where I can select how fancy effects I want and choose none, the theme returns to a Gnome theme, is that intented?

---

### Post by overdrank on 2008-04-19
> **LasseNC said:**
> Am I supposed to run that everytime I start up?

When I right click on my desktop and navigate to the fan where I can select how fancy effects I want and choose none, the theme returns to a Gnome theme, is that intented?

HI and if you have added emerald to the start up session then no. Yes if you select none in the effects then it will revert back to metacity.

---

### Post by LasseNC on 2008-04-19
> **overdrank said:**
> HI and if you have added emerald to the start up session then no. Yes if you select none in the effects then it will revert back to metacity.

I have added the "emerald --replace" to sessions, I am unsure of how to add the program itself.

---

### Post by forrestcupp on 2008-04-19
Emerald only works if Compiz (your visual effects) is turned on.  If you aren't starting with visual effects turned on, then the **emerald --replace** in your sessions is worthless.  You need to be starting with visual effects on in order for emerald to work.

---

### Post by LasseNC on 2008-04-19
And how do I do that? I have compiz ofc. I just want to know how I add the programs to the start folder.

I can't find compiz on my system, though I can through Synaptic see that it is in fact installed on the system.

---

### Post by overdrank on 2008-04-19
> **LasseNC said:**
> And how do I do that? I have compiz ofc. I just want to know how I add the programs to the start folder.

I can't find compiz on my system, though I can through Synaptic see that it is in fact installed on the system.

HI and what version of ubuntu are you using, 7.04 feisty, 7.10 Gusty? You can start compiz with the alt, F2 keys and enter ```
compiz --replace
``` To add to your start up under system, preference, sessions. Then click add and those are the command  with the --replace.

---

### Post by LasseNC on 2008-04-19
> **overdrank said:**
> HI and what version of ubuntu are you using, 7.04 feisty, 7.10 Gusty? You can start compiz with the alt, F2 keys and enter ```
compiz --replace
``` To add to your start up under system, preference, sessions. Then click add and those are the command  with the --replace.

Didn't get that last bit. I added emerald the way you described, I am to add compiz the same way?

---

### Post by overdrank on 2008-04-19
> **LasseNC said:**
> Didn't get that last bit. I added emerald the way you described, I am to add compiz the same way?

HI and yes you can or you can just use that command to see if compiz  will start. I see you are using a ATI graphics card and what version of ubuntu?

---

### Post by LasseNC on 2008-04-19
> **overdrank said:**
> HI and yes you can or you can just use that command to see if compiz  will start. I see you are using a ATI graphics card and what version of ubuntu?

The latest, just reinstalled today. Gutsy

---

### Post by oboedad55 on 2008-04-19
> **LasseNC said:**
> The latest, just reinstalled today. Gutsy

Not quite sure where you are now, but as far as Emerald goes, once you have compiz installed just make sure the windows decoration plugin is installed then put in the command section. emerald --replace.

Cheers,

---

### Post by forrestcupp on 2008-04-19
Just go to System->Preferences->Appearance and click the Visual Effects tab.  Then choose anything other than None, and if it works, Compiz will be running.  Compiz is the name for the visual effects.  If this works, then Compiz should just automatically come on from now on.  If it doesn't work and it reverts back to None, then we'll have to figure out how to get it to work.

Do you really have an ATI card?  I didn't see anywhere in this thread that you mentioned that.  If so, ATI cards are a little trickier to get the visual effects working.  But once the effects are working, your emerald entry in your sessions will start working when you boot up.

---

