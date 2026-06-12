---
title: "got a weird couple of errors when trying to update and upgrade 16.04"
date: 2017-04-17
forum: General Help
---

### Post by acuratlgtlm on 2017-04-17
okay, so to start, I started by doing ```
sudo apt-get update
``` put in my password, it started to do its thing, until it spit out this scunge: ```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```. so far, all of the help i've received outside of the forums here have given me advice for older versions of Ubuntu, and when asked for advice specific to 16.04, I am told "Oh, I don't work with that version." cue the facepalm.

also, first time using Ubuntu again in a few years, the r/Ubuntu subreddit is full of confused Windows users who don't realize what sub they're in, so it's slightly useless, so any *actual* help would be fantastic. I just hope my rig doesn't get kerfuffled because of these errors.

---

### Post by kc1di on 2017-04-17
try this in the terminal ```
sudo rm /var/lib/apt/lists/lock
```
try update again.

---

### Post by lisati on 2017-04-17
Also make sure that you don't have something like Software Centre, update manager or synaptic running at the time you try the update.

---

