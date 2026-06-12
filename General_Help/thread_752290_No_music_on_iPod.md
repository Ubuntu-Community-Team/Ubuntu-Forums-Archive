---
title: "No music on iPod??"
date: 2008-04-11
forum: General Help
---

### Post by neonmagnolia on 2008-04-11
I am very new with using linux on my ipod, and am currently searching for the best available management program. I had about 33GB on my iPod that I loaded from iTunes on Windows before I switched to Ubuntu. I just tried syncing my iPod with my music directory in gtkpod, since I got about 5GB of music from a friend.

The problem is, my iPod says it now has about 38GB of music on it, however, it says I have no music. And no videos, either. What happened?? When I plug my iPod in I can play the files in Rhythmbox and they all show up in gtkpod even, but still nothing shows when its unmounted.

I have an 80GB iPod video, 5th generation, I think.

---

### Post by swimmerbody on 2008-04-11
the database is corrupted.  Use gtkpod and run it as su.  make sure you have the correct libraries.  then it works

---

### Post by gali98 on 2008-04-11
Before you do as the user above suggested, I suggest backing up everything so you won't lose it if someting goes wrong... :)
Kory

---

### Post by neonmagnolia on 2008-04-11
> **swimmerbody said:**
> the database is corrupted.  Use gtkpod and run it as su.  make sure you have the correct libraries.  then it works

Sorry, not sure what you mean by all that. I don't really know anything about anything here.

Files are already backed up, check.

---

### Post by neonmagnolia on 2008-04-12
K Just kidding, it's actually a sixth generation iPod. Model MB147LL. After doing some Google searching I've found that maybe this iPod isn't terribly compatible with linux... Any suggestions, or am I going to have to switch back to Windows to make this thing work?

---

### Post by Incompetnce on 2008-04-16
I have this same problem. gtkpod and rhythmbox both think there is music on my ipod, but  the ipod itself doesnt. i have gone to the file path and listened to the mp3 on the ipod, so it is physically there but the thing doesnt seem to recognise this fact.

its a brand new ipod, i've tried adding an album through gtkpod. everything works except the ipod recognising there is music on itself. what can i do about this?

---

### Post by BandD on 2008-04-16
The good old people at Apple have added a kind of 'protected' database to newer ipod models.  If the ipod firmware detects that something has changed with out proper approval (say from itunes) then the Apple firmware thinks the database is 'comprimised' and will refuse to reconginze it.  They say it's for added 'stablity', perhaps they mean to stablize their monoply or some such. 

Basically it has made it much harder for 3rd party developers to modify the ipod database.   All the files are fine.  It's just that the firmware thinks 'Oh know, some non-Apple related tool has touched me, I have cooties now.  I can't function!!!!'

Frustrating.  Basically the only way to fix it is to boot to windows or os x and restore it with itunes.  

You could try this[ http://ubuntuforums.org/showthread.php?t=619615]("http://ubuntuforums.org/showthread.php?t=619615")

---

