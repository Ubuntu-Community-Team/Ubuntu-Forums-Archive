---
title: "Loving Ubuntu, having a few problems though..."
date: 2004-11-09
forum: General Help
---

### Post by stratking on 2004-11-09
Hey all,  I have been using Ubuntu on my laptop for about a month or so now and have been loving it.  In the past week or so however I have been running into a few problems that I can't really fix. 

First, whenever I try to either shutdown or logout, X dies out but then the machine just hangs.  Everytime I want to logout or even reboot I have to do a hard shutdown.  

Also, I have noticed a signifigant drop in speed when connected to my wireless connetion at home.  The laptop is dual booted w/ Win XP and XP gives normal speeds but as soon as I boot into ubuntu it takes roughly about 15-25 sec. for each page to load and about the same amount of time for gaim to log in.  I tried the Firefox hacks to speed it up and also read somewhere how to disable IPv6 but neither seemed to do anything.  I am using a netgear ma401 wireless card and I believe the router is a Dell TrueMobile 2300 although I am not certain of the model number.  

When open totem the program seems frozen, I can't click on any of the toolbars at the top nor can I drag any videos onto the player.  All I can do is D-click a file and totem will come up and play.  

I am also have a problem getting XMMS to start.  Whenever I try to run the program, I see the window for it come up in the taskbar at the bottom but quickly goes away and the program never loads.  When I run it from the terminal I get the error message but I am not on the laptop right now so I will have to post the error once I get home.

Once last thing.  When using synaptic, I show that I the current firefox version I have installed is the 1.00 pre release but when I go to help > about in the browser it shows that I am still on 0.93.  

Anyway familiar w/ any of these problems?

---

### Post by TravisNewman on 2004-11-09
First off your networking problems may not be because of the network. I had the same problems on a wired network. It would take 20-30 seconds to resolve the domain name. I reinstalled because I wanted to do some partition changes, and when I reinstalled it was fine. Hopefully you won't have to do that to get it to work.

If you notice, the line about the firefox version in synaptic says something like 1.0PR-reverted-to-0.93. I don't know why they reverted it, but they did.

Hope everything goes well for you, and welcome aboard!

---

### Post by jdong on 2004-11-09
Firefox was reverted just a few days prior to Warty's release, because there were reproducable bugs with Firefox 0.10PR closing down suddenly, usually on popups.

I don't see those problems with 1.0RC1 in the Hoary Development branch yet...

---

