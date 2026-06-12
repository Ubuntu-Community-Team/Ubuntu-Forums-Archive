---
title: "Evolution crashes upon Calendar View"
date: 2007-12-06
forum: General Help
---

### Post by inzeo on 2007-12-06
Hey Everyone,

Just recently, Evolution has been crashing with a "segmentation fault" when I attempt to view the Calendar.  Any try of restarting Evolution after this error causes it to startup and quit right-away.  In order to get it working again, I have to completely remove Evolution and start over, with the problem occurring again upon reinstallation.  Does anyone have any suggestions?  Thanks in advance! 

P.S. I'm running Gutsy (7.10)

---

### Post by castironpants on 2008-01-10
I have the same problem! Can anyone help?

---

### Post by c_cammann on 2008-01-11
I also have the same problem, but with contacts instead of Calender. Have you found any solutions?

---

### Post by castironpants on 2008-01-11
It's by no means a fix, but for my problem I can get around it by using Dates, which writes to the backend without using the frontend. Your your contacts problem, try the program Contacts.

---

### Post by _oOMOo_ on 2008-01-11
I have this problem in both Gutsy and Hardy testing, both recent installs, and even after setting up a new user. What a shame, evolution seems to be able to do everything I wanted, except run.
[COLOR="Red"]
**EDIT: I discovered that the Aurora GTK theme / engine I was using was causing the problem. I switched back to Clearlooks and Evolution is playing ball now.**[/COLOR]

---

### Post by castironpants on 2008-01-11
> **_oOMOo_ said:**
> I have this problem in both Gutsy and Hardy testing, both recent installs, and even after setting up a new user. What a shame, evolution seems to be able to do everything I wanted, except run.
[COLOR="Red"]
**EDIT: I discovered that the Aurora GTK theme / engine I was using was causing the problem. I switched back to Clearlooks and Evolution is playing ball now.**[/COLOR]

Oh my god! It worked! Thank you!!!!

But I liked my theme. What's the deal?

IDEA: Can we have everything in Aurora except Evolution? I know you can have the admin account have a different theme so all your sudo windows look different. Can we define a theme that doesn't use aurora for evolution?

---

### Post by _oOMOo_ on 2008-01-12
> **castironpants said:**
> Oh my god! It worked! Thank you!!!!

But I liked my theme. What's the deal?

IDEA: Can we have everything in Aurora except Evolution? I know you can have the admin account have a different theme so all your sudo windows look different. Can we define a theme that doesn't use aurora for evolution?

Yes I like Aurora too, it's a shame - I've left a comment on the Aurora page on Gnome-look; maybe the dev will be able to code a fix for the next version.

The reason the sudo windows look different is that those windows are owned by root and take their settings from root - there may be a way to set up evolution to use a different engine but I'm not sure how! :)

---

### Post by c_cammann on 2008-01-14
My problem must be different.... still crashes :(

---

### Post by caprenter on 2008-01-17
I've been having this issue this morning. The calendar has just been crashing evolution, and once crashed the whole desktop. I've only been trying to add and edit appointments.

I'm using Evolution 2.12.1 on Gutsy, and 

I was using the default (?) theme: 'Human'

After reading this thread I switched to 'clearview' and there haven't been any problems so far. (I have added and edited existing callendar appointments without a crash!) 

I will report back if I do get problems.

UPDATE: Well it crashed again, when changing form mail view to calendar view. I tried changing the theme at the time to see if that helped, but it remained crashed. Could close evolution (pop up box 'Force Quit') and restarted and the calendar is fine again - even though I am now back to 'Human' theme) Ho Hum!

---

### Post by robinm on 2008-02-11
I am also having this problem after I updated my packages. The theme that I use does not influence this bug, tried a couple of themes... :(

Hope this problem can be solved somehow...

---

### Post by it_broke_again on 2008-05-01
I used Evolution one time since installing Hardy Heron from scratch. It worked that one time and then the last time I selected Calendar view and it crashed. After that, it crashes every times I start it no matter what theme I'm using.

Typing:

```
evolution
```

in the terminal gives me nothing-- just a blinking space and it's unresponsive-- no error message, no nothing. I tried:
```

sudo evolution
```

in the terminal and evolution will work but I'm not interested in using my root account for it.

If there's any specific terminal output or error messages you'd like me to provide, just let me know.

**UPDATE**
Using the Synaptic Package Manager, I reinstalled "evolution" only and it did successfully load, however, after attempting to switch the view to "Calendar", it became unresponsive again and crashed. Every time I attempted to start it after that point, it would crash.

After trying that, I reinstalled it again, re-entered my e-mail information and I attempted to work in Offline Mode and then switch to the Calendar view-- which worked. After switching it back and forth between Online and Offline mode in different views, it hasn't crashed yet. I switched to a different theme and tried evolution again and it didn't crash. It seems that for me, reinstalling "evolution" only in the Synaptic Package Manager worked. I did not have anything saved so I didn't need to back anything up beforehand-- if you have things saved, back them up before reinstalling as I am not sure how reinstalling "evolution" will effect user files.

---

