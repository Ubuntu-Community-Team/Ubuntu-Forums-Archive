---
title: "Muine .83 + Audioscrobber"
date: 2005-06-30
forum: General Help
---

### Post by jadugarr on 2005-06-30
Has anyone here upgraded to muine .83 through the backports that also uses the audioscrobber plugin (current version is 0.1.5)?  After I upgrading i get segmentation faults that crash muine when the audioscrobber plugin is turned on.  I think its crashing when it tried to connect to the audioscrobber server.  Turning off the plugin and then restarting muine seems to be a temporary fix.

Has anyone else experience this problem?

---

### Post by Majlo on 2005-06-30
I have Muine 0.8.3 from backport and audioscrobbler plugin worked fine..
Try reinstall Muine & plugin

---

### Post by jadugarr on 2005-06-30
I have already tried deleting the plugin and reinstalling it, but that didn't help.  I think it might have something to do with the server being unreachable at the time and it crashes ... because it crashes when its about to send the song info to audioscrobber.

I'll try reinstalling them both again and see if that helps.

---

### Post by Majlo on 2005-07-01
Damn today i have same problem as you.I tried downgrade muine to 0.8.2 , then i tried compile 0.8.3 from source and always segmentation faults :-( 
Maybe problem with audioscrobbler site

---

### Post by jadugarr on 2005-07-04
I think it only crashes when the website is down or something.  Anyway, I have disabled the plugin for now and everything works ok.  Maybe there will be an upgrade to the plugin in the near future.

---

