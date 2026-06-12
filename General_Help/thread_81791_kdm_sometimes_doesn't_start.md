---
title: "kdm sometimes doesn't start"
date: 2005-10-25
forum: General Help
---

### Post by GoldBuggie on 2005-10-25
First the nice usplash shows and runs thrue the necessary loading of services etc. Then when everything has been started and its time to go from the usplash to the kdm login I get the text login. This happens from time to time and is in that sence annoying. When I restart it oftens gets to the kdm and all is well...but it happens to often.

Any thoughts?

---

### Post by coolblue on 2005-10-25
Hey dude i have the SAME EXACT PROBLEM!! Methinks Kubuntu Breezy is REALLY BUGGY!! I'm so disappointed....hoary was so much better...and it booted & shutdown so fast!!

I also have this problem that when I shut down, often I dont see any text roll by but only a blank screen.

I'm thinking of doing a fresh install of kubuntu hoary...unless this problem  gets fixed....

Plz HELP us!!

---

### Post by mlomker on 2005-10-25
I have a half-dozen machines running Kubuntu Breezy and no major problems.  If you did an upgrade instead of a fresh install then I definitely recommend the fresh install...my Hoary upgraded machine was a mess.

---

### Post by GoldBuggie on 2005-10-25
Well...doing a fresh install isn't an option for me at this moment. Have no place to move the things I have in my home dir. too. Isn't there another option...something that is similar to a fresh install or something? And I've personilized this computer and doing it all over again takes alot of time. But there has to be some setting somewhere...some time setting perhaps?...feels like some things in ubuntu are made for non laptop higher then 900MHz ppl. I can live with that since that is just some tweaking for me to change...but the login is really annoying.

btw...i really appreciate you taking the time to answer...ty

---

### Post by fannymites on 2005-10-25
Maybe checking the logs may give you some idea?  Applications>System Tools>System Log I think (I customized my menus so I can't be sure).
Or maybe typing dmesg in a terminal would indicate if something wasn't working right on boot up.

---

### Post by coolblue on 2005-10-26
I did clean install of ubuntu..then installed kubuntu-destop....how could that create any problem? :(

---

### Post by JFK on 2006-01-18
Hi there,

I had the same problem that kde sometimes just wouldn't start. I don't think this is a kde problem but I think it's a problem with the xserver.  At the startup from kde my monitor always tried to reinitialise (wich it never did in Fedora).  When I looked at /etc/X11/xorg.conf I noticed that my monitor wasn't recognized by Kubuntu. It used some generic settings wich are incorrect for my monitor. 

The solution: Fill in the right refresh rates in xorg.conf. (I got the right refresh rates out xorg.conf from a Fedora Backup):smile:

---

### Post by limit223 on 2006-01-19
On top of above I would add that I've read right in this forum about kdm kubuntu theme would be buggy...try to change the theme and see the difference.

---

### Post by Peter76 on 2006-01-21
I have sort of the same thing; sometimes get the login prompt instead of kdm... But when logged in at the prompt and did startx, it said xserver already running... So I did alt+f7 and there was kdm.... Still weird though

---

