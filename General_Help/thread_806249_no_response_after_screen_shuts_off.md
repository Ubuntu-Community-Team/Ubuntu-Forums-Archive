---
title: "no response after screen shuts off"
date: 2008-05-24
forum: General Help
---

### Post by jellylogix on 2008-05-24
When my screensaver runs, and then after a period of time, it shuts the screen off, when i wiggle the mouse to bring it out of this, the screen stays black, the backlight comes on (cause i can see it on the sides of the LCD) and it doesn't respond. When the screen shuts off, music also stops playing. Is it sleeping? and if so why can't it resume. 

I have a HP DV6000 laptop with Hardy installed.

To get it out of this, i simply hold down the shutdown button until it powers off. Also some times I can just press the power button, I hear a beep and a couple seconds later (after hard drive activity) the computer shuts off.

---

### Post by joshsmith on 2008-05-24
have a look in system>preferences>power options to see if you computer is ever set to go to sleep or hibernate

if the lights change on your computer indicating the state of your computer then this may indicate sleeping or hibernating. if it tries to hibernate but fails you may get weird results, but without lights changing. hibernate and suspend is quite difficult for linux to do as every computer does it differently, but it is getting better 

for me if my computer goes to sleep it sometimes pauses on the screen waiting for my password but the screen doesnt refresh, so if i just type my password blindly and press enter, i get to my desktop. worth a try

look at this: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) instead of holding down the power button, a lot safer

---

### Post by jellylogix on 2008-05-26
ok your tip kinda helped in that is, when the screen is not responding, i make it GO into sleep ('fn button' + F5) and then press enter, it will put it into sleep, immediatly bring it out of sleep, and then display a pure white screen with my cursor. From there i can move my sursor around the screen until it changes to the 'I' looking cursor, showing me it has found a textbox (my password entry). I "blindly enter my password" and it refreshes the screen and Voila! my desktop. It's a hassle, but it sure beats restarting... and going back to Windows.

---

