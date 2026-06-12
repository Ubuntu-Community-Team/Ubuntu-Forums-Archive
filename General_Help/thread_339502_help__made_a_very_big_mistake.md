---
title: "help  made a very big mistake"
date: 2007-01-15
forum: General Help
---

### Post by will61 on 2007-01-15
I've only been using Ubuntu edgy eft for about 3 months so far I've successfully setup beryl and mythtv 

Up until today Mythtv was working just fine all that was left to do was setup my remote I tried to install Lirc without much success 

So I decided to start the Lirc installation from scratch and marked all Lirc components for "complete removal" in synaptic package manager 

To my complete horror I found that it also uninstalled Mythtv and totem media player 

Is there a restore function in synaptic package manager or any sort of code I can enter in terminal to restore mythtv ????

I really don't want to start all over installing Mythtv

---

### Post by will61 on 2007-01-15
Here is the output from my history in synaptic package manager

Commit Log for Tue Jan 16 13:50:46 2007


Completely removed the following packages:
liblircclient0
lirc-modules-2.6.17-10-generic
lirc-modules-source

Removed the following packages:
libmyth-0.20
lirc
mythbrowser
mythcontrols
mythdvd
mythflix
mythgallery
mythgame
mythmusic
mythnews
mythphone
mythplugins
mythtv-backend
mythtv-frontend
mythtv-themes
mythvideo
mythweather
totem-xine

This totally blew me away seeing I'd only selected Lirc for removal

---

### Post by will61 on 2007-01-15
Thank you in advance to all who have read this thread 

Although I didn't find an option anywhere to be able to restore Mythtv I just reinstalled it and it was all ok seeing my Mythconverg DB was still intact

---

### Post by hikaricore on 2007-01-15
Most programs store data in seperate directories from the install.  Either in your home directory "~" or in another place.
Removing software in linux "usually" does not mean the loss of said data.

It's a pretty safe bet by just installing back the packages you need, that they will work just like before.

---

### Post by will61 on 2007-01-15
Yes you are indeed right, it's all back up and running just the way it was before.

After this big scare I think I'll read up on how to do a full system backup just in case I have anymore mishaps 

I've only been using Ubuntu for three months and I'm having a great time setting it up and customizing it  

I plan to be 100% windows free in the next 18 months or so

---

