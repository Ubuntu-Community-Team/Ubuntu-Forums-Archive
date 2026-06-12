---
title: "aMule upgrade"
date: 2006-07-31
forum: General Help
---

### Post by moeFinley on 2006-07-31
I've been having a problem with aMule 2.1.0 that it crashes after 5-6 hours.  There was a post on the aMule forum about this exact problem and the solution apparently was to install wxGTK.  But I have upgraded to wxGTK 2.6.3 (patched) for Ubuntu 6.06 and aMule still crashes after a few hours.

So I tried to upgraded to aMule 2.1.2 to see if this would help, but now aMule doesn't load at all.  I get the following in the terminal

amule: /usr/lib/libwx_gtk2u_core-2.6.so.0: version `WXU_2.6.2' not found (required by amule)
amule: /usr/lib/libwx_gtk2u_core-2.6.so.0: version `WXU_2.6.3' not found (required by amule)

Does this mean I don't have wxGTK installed correctly?  Is there a more acurate way of checking I have wxGTK installed correctly? Currently I'm just looking in Synaptic.

Thanks for any help

---

### Post by yaztromo on 2006-08-01
You could try upgrading to 2.1.3

Make sure you have packages amule and amule-common installed

[http://www.ubuntuforums.org/showthread.php?t=224474&highlight=AMULE](http://www.ubuntuforums.org/showthread.php?t=224474&highlight=AMULE)

I have wxgtk from the standard dapper repositories and it works okay using that. I would try to just use that and see what happens.

---

### Post by moeFinley on 2006-08-01
I just bought a new graphics card and now 2.1.2 is running?!

I'll wait and see if it lasts more that 6 hours

---

