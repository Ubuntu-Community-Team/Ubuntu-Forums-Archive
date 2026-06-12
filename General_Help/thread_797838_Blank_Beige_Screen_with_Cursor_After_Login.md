---
title: "Blank Beige Screen with Cursor After Login"
date: 2008-05-17
forum: General Help
---

### Post by ErmyDermy on 2008-05-17
After I enter my Username and Password it just goes to a Blank Beige Screen with Cursor. I have tried Failsafe login, but I get the same problem. And this is on a new installation, and my first login. I am a newbie to Ubuntu so I would have no idea what is causing the problem, allthough I wonder if it is something to do with the Graphics card driver. (I have a ATI Radeon X1650 Pro)

---

### Post by foska on 2008-05-18
I have a similar problem!

---

### Post by AlbertTatlocksCap on 2008-05-18
Ok - I had the same problem after a fresh install install of 8.04 onto a scsi disk (apparently it seems to affect scsi and USB devices)

I used this to get around it for now

CTRL+ALT+F1

Login in text mode

sudo rm /tmp/.X0-lock

startx

It should then start up OK 

Then set Automatic login by:

System>Administration>Login Window>Security and then check Automatic Login

Ok - this means that you can only login with one username and it will be automatic so no login window for password - but it works and I suspect/hope there will be a fix in the near future

Hope it helps

---

### Post by ErmyDermy on 2008-05-18
When I press CTRL + ALT + F1 I just get a totally black screen, until I press CTRL + ALT + F7 which goes back to how it was before.

---

### Post by AlbertTatlocksCap on 2008-05-19
Ok try CTRL+ALT+F2 instead and see if you get to a black screen to login in text mode

Hope it solves it for you

---

