---
title: "Emerald help"
date: 2008-05-17
forum: General Help
---

### Post by speedemonV12 on 2008-05-17
Hi guys.. So i am pretty new to ubuntu, i used it about a year ago, and now im getting back into it. I have it tripple booted on my macbook pro with leopard and xp pro. Anyways, i love to customize the look of my desktop, so I downloaded some emerald themes, cause they are pretty cool. It took me forever to figure out how to apply the themes. But this is where i am at, 

I have a theme selected in emerald, 
to get it to work, i have to type emerald --replace in terminal. 
Then the theme shows up, but if i close the terminal window, I have no window border, and i have to type emerald --replace in terminal again. So that is kinda a pain, anything I can do about that?

The second thing is: what if i get tired of an emerald theme, how can i get it so that i go inter appearance under System Preferences, and select a theme and window border from there to work. I cant get those themes to work now. how can i switch between emerald, and the gnome default theme manager?

---

### Post by badfish591 on 2008-05-17
i have the exact same problem, i have given up on emerald because of it.
but if anyone knows why this is happening that would be awesome

---

### Post by rich257 on 2008-05-17
To keep emerald running you can do one of two things:
[LIST=1]
[*]In the terminal append an ampersand to the line to detach the process.  So the command becomes "emerald --replace &".   You will need to run this each session that you want emerald running in, or
[*]Auto start emerald with the session.  Go to System, Preferences, Sessions then Add and enter "emerald --replace" as the command
[/LIST]

---

### Post by badfish591 on 2008-05-17
> **rich257 said:**
> To keep emerald running you can do one of two things:
[LIST=1]
[*]In the terminal append an ampersand to the line to detach the process.  So the command becomes "emerald --replace &".   You will need to run this each session that you want emerald running in, or
[*]Auto start emerald with the session.  Go to System, Preferences, Sessions then Add and enter "emerald --replace" as the command
[/LIST]

the first option doesn't do anything, the entire border still disappears as soon as i close terminal. However adding in sessions did allow it to start up and run all the time. this is how i would have originally set emerald up, but when it started acting wierd when i tried to test run it from terminal i never got that far.  

thank you.

---

### Post by Enlitend on 2008-05-17
@badfish591
You might as well put "emerald --replace" in 
CCSM-> window decorations-> command
reboot and test it out.

---

### Post by tommyhakinen on 2008-05-18
Use Fusion-Icon. To install:
> sudo apt-get install fusion-icon

Access it from System Tools > Compiz Fusion Icon
On the Notification Area, right click on the Compiz Fusion Icon go to the "Select Window Decorator", and change it to Emerald.

---

### Post by NightwishFan on 2008-05-18
Press alt+f2 and type the command, that way it keeps running without a terminal open. Otherwise just add it as a start-up app as was said.

---

### Post by Deeta on 2008-05-18
> **Enlitend said:**
> @badfish591
You might as well put "emerald --replace" in 
CCSM-> window decorations-> command
reboot and test it out.


I tried that but it seems compiz just ignores the string at this setting. (or rather it just started the default decorator again :-/)

---

### Post by speedemonV12 on 2008-05-19
ok, so i figured out how to get it to always start up.. .i added it to the system startup.. but now, for my second problem

The second thing is: what if i get tired of an emerald theme, how can i get it so that i go inter appearance under System Preferences, and select a theme and window border from there to work. I cant get those themes to work now. how can i switch between emerald, and the gnome default theme manage?

---

### Post by Deeta on 2008-05-19
You can switch using the 'compiz fusion icon' tool :D

and you can use the 'emerald-theme-manager' to switch themes when you get bored of a certain theme you have :D

I love emerald as it allows me to create my own super-colourful minimalistic theme :D
(typical minimalistics are all grey and dark and drab ^-^ Wheee)

---

### Post by speedemonV12 on 2008-05-19
that worked! thanks!... 

.. deeta, any of your themes up on gnome-look?

---

### Post by Deeta on 2008-05-19
@themes: Nah, I typically modify existing ones to match my preferences :D The one I based my modifications on was 'tankerdog'. I think I got it from the now defunct Beryl-themes website.

---

