---
title: "Ubuntu version upgrade gone wrong"
date: 2019-08-07
forum: General Help
---

### Post by caymannn on 2019-08-07
Hi, 
I have an old laptop that's currently on ubuntu 14.4 that I would like to upgrade to 18.4

A couple days ago I tried to run some commands I found that were supposed to upgrade me to 16.4, I can't remember the exact message but the terminal window said there were errors. Upon restarting I'm still on 14.4, my laptop is in a 
very low resolution [480p?], my wifi connection doesn't work anymore and even using an ethernet cable I can't get an internet connection.

After plugging in the cable I try to ping 8.8.8.8, I get the response

"An error occurred when try[sic] to run 'ping'     /bin/ping ping -b -c 5 -n 8.8.8.8"

I don't really know where to start, I suppose getting the internet connection working is the first step? Any suggestions on how I go about that? Or should I just wipe it completely? (if it wasn't obvious yet, I'm not experienced with linux)

I should add that the 14.4 version has never really worked properly (I never got the time on the top right, gedit couldn't open, media player couldn't open either)

---

### Post by &amp;wP*!) on 2019-08-07
14.4 to 18.4 is a huge difference, lots of things might have been changed. Easiest way for me: backup your documents from Documents, Downloads etc. folders, i.e. private data and re-install 18.4.

---

### Post by CatKiller on 2019-08-07
> **caymannn said:**
> Any suggestions on how I go about that? Or should I just wipe it completely? (if it wasn't obvious yet, I'm not experienced with linux)

I should add that the 14.4 version has never really worked properly (I never got the time on the top right, gedit couldn't open, media player couldn't open either)

14.04 has passed its End of Life, and your install is broken, and has apparently always been a bit broken.

You'd need to do two separate full upgrades of that broken system, which currently has no Internet, and each of which would under ideal circumstances take a couple of hours. A fresh install of 18.04 will take about half an hour.

It seems like an easy decision to me.

Since you've described it as "an old laptop," looking at a lighter desktop like Xubuntu or Lubuntu might be a good idea.

---

