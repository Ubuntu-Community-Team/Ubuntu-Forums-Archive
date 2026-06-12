---
title: "Can't see desktop, can't change resolution ..."
date: 2007-02-15
forum: General Help
---

### Post by joenearns on 2007-02-15
I have ran a linux in the past and actually had a server in my living room back in 1996 after configuring an old 486DX 33MHz Dog, hahaha.  I loved it and was serving up my own web page from the (mind you, it was only a 28.8 bandwitdh, back when patience was a must!)

I recently discovered this Ubuntu and I really like it so far.  However, I only have one choice displayed when I go to Display Resolution 480X600(???).  I can see a damn thing, all the choice buttons are off screen and I have to access the windows menu (Alt + Space) and do a move any time I want to change the location of a window to answer questions.

I'm running 6.06 on a W3052 eMachine,2 GHz, 768MB of RAM and my monitor is a Samsung 790DF 15". I've never had a problem with the monitor and is capable of displaying several if not all common resolutions.  How do I tell Ubuntu that???????

I usually can figure these things out but after a week of cursing, I NEED HELP!!!!

Any suggestions.

I'm not a forum type guy, or haven't been in the past.  That will change now that I am retired and have lots of time on my hands.  So if you do have a solution or know a location I can find one, please email me at [email]joenearns@cablemo.net[/email] after answering the thread.

Thanks guy & gals, I look forward to bending my learning curve here and meeting new geeks, hahaha!

HELP ME, PLEASE!!!

Jospeh P. Nearns

---

### Post by igknighted on 2007-02-15
Do you know what type of graphics card you have?  This is the most likely culprit.  If it's nvidia or ati, then it should be as simple as installing the proper drivers.  If it is something else, then it might need an xorg.conf edit to set the resolutions properly.

---

