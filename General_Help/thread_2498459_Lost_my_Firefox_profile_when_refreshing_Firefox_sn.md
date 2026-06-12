---
title: "Lost my Firefox profile when refreshing Firefox snap"
date: 2024-06-14
forum: General Help
---

### Post by wgarcia on 2024-06-14
I'm with Ubuntu 24.04. I've just refreshed the Firefox snap and got version 126.0.1. When I restarted Firefox, it told me that I had to create a new profile because I was using an old version. I tried different things to get back to the profile I was using before refreshing, like starting the Firefox Profile Manager (for instance "firefox -p" from the command line) and trying to import my old profile which I still can see in the snap profile folder. I couldn't recover the old profile no matter what I tried.

Did I do anything wrong?

Is this a problem with the last Firefox version or a problem with the snap packaing? 

(no snap flaming please, just take for granted I want to use Firefox packaged as a snap, and I know I can use it and how to use it as a deb or flatpak, but I don't want to)

---

### Post by #&amp;thj^% on 2024-06-14
> **wgarcia said:**
> 
Did I do anything wrong?

Is this a problem with the last Firefox version or a problem with the snap packaing? 


Nothing to do with you, it's hard to say if it is snap or firefox, is your old profile still on your system?
```
about:profiles
```
I'm currently on version 127, and have not seen or had any problems with a non snap firefox

---

### Post by wgarcia on 2024-06-15
I did try to access my old profile with "about : profiles" or starting directly the firefox profile manager from command line with "firefox -p". My old profile is indeed still in the system, but this version of Firefox tells me that it has an "old format" and it has to create a new profile.

I recreated the profile already (I use an extension called "Cloud dials" which is very useful in this type of cases to recreate fast access to all my favorite sites, and the other main important part of my profile is "save passwords" and "certificates", those I had to recreate from scratch). But I'm worried the same happens in two other systems of mine. Well, now that I have a working profile in this system, maybe it is no so bad if it fails in the other systems because I can copy over this working profile.

---

### Post by wgarcia on 2024-06-16
I did try to access my old profile with about : profiles or starting directly the firefox profile manager from command line with "firefox -p". My old profile is indeed still in the system, but this version of Firefox tells me that it has an "old format" and it has to create a new profile.

I recreated the profile already (I use an extension called "Cloud dials" which is very useful in this type of cases to recreate fast access to all my favorite sites, and the other main important part of my profile is "save passwords" and "certificates", those I had to recreate from scratch). But I'm worried the same happens in two other systems of mine. Well, now that I have a working profile in this system, maybe it is no so bad if it fails in the other systems because I can copy over this working profile.

---

### Post by psychohermit on 2024-06-16
What about Firefox's sync function?  That should restore your passwords and bookmarks.  I don't know about your certificates.

--glenn

---

### Post by wgarcia on 2024-06-16
Sync is a good suggestion, thanks.

Maybe the problem was that I've been updating this system since, I think, 2013 or 2014, without any reinstallation. Maybe the format of the profile installed back then became obsolete.

---

### Post by wgarcia on 2024-07-16
I lost again my Firefox profile when I refreshed my Firefox snap to the last version offered in my system (24.04, everything updated). It told me again that the profile was from an older version and refused to open Firefox after the update.

I have now removed-purged the Firefox snap and installed it again. I have recreated my profile again. I still don't know why this is happening to this system (my desktop computer). I have two laptops with the same Ubuntu version and I'm not seeing this.

---

