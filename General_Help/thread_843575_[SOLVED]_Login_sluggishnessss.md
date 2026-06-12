---
title: "[SOLVED] Login sluggishnessss"
date: 2008-06-28
forum: General Help
---

### Post by Ekeluo on 2008-06-28
Well, I'm used to slow PCs but this is a bit irritating. My Ubuntu 8.04 now takes several minutes to login. From password typing+return key to hard drive light finally off is about 1:57 now. I don't think it should take this long, I have kde installed beside and I'm sure it takes less than a minute to get thru the same. This is an ubuntu installation with the kde added on, I'm running compiz fusion with desktop wall, 3 workspaces on a PM 1.6ghz laptop with 768mb ram. AWN and google desktop are the only extras that start with gnome desktop. Any useful tips will be appreciated.

---

### Post by ajgreeny on 2008-06-28
That is a long time with your specs.  Should be about 30 secs, I reckon.  Have you tried looking in your system set up with bum (Boot up Manager) which can be installed with synaptic or whatever kde uses, and will allow you to turn of things you don't need.  Also check that this is not a network problem, with the system waiting for a slow network to start up.

---

### Post by steak-sandwich on 2008-06-29
I have the same problem with a dual core 2.2GHz, 2GB Ram,....
I installed 8.04 yesterday and I already have this problem. 
Right after the login, it takes too long until I get to my desktop. Instead I have to watch this orange screen......awesome!
I already had this problem with 7.10 and I saw in this forum that many people had the same problem and I was told they will fix it in 8.04.

---

### Post by lukjad on 2008-06-29
Could you go to System->Administration->Services and tell us what is running at startup? If you can get rid of a FEW things it might help your start up time some. Make sure you know what you are removing. Don't just remove things you think you don't need or your system won't start at all.

---

### Post by steak-sandwich on 2008-06-29
okay here it is. check the screenshot.
I was surprised that it happened even after the first login after installing ubuntu. I didn't expect that.

---

### Post by Ekeluo on 2008-06-30
Screenshots below of startup and services settings. Experimenting, I created a new user and I could login much faster (though I didn't restart and second logins are always faster). And to reiterate, this is gnome I'm talking about. KDE is installed right beside it (same installation, same partition) but takes under a minute to login, with google desktop and compiz, same settings. WHY?

---

### Post by Ekeluo on 2008-07-20
Solved my problem by creating a new user and switching over. I suppose it kept lots of useless stuff under my old user profile.

---

