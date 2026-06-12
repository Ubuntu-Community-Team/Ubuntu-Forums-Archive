---
title: "The Unsolvable Crash? (Gaim)"
date: 2007-07-10
forum: General Help
---

### Post by Angelus7 on 2007-07-10
Hi.  I'm in Dapper Drake, or Ubuntu v. 6.06LTS, and EACH AND EVERY SINGLE TIME I try to log on to my MSN account, it crashes immediately after getting to the buddy list...

This happens without fail..all....the....time.  It is starting to get me rather angry..to the point where I'm wishing for Windows again.

Could someone PLEASE HELP ME?  I've searched all over these forums and the internet, and I haven't really found a clear answer.  I am using the Gaim that came preinstalled with this Ubuntu version.  I have -not- updated yet, because I haven't found a thread that tells me how.  (And yes, I'm a noob ;-P)

Peace.

---

### Post by Angelus7 on 2007-07-10
Bump-

Anybody?

---

### Post by DoktorSeven on 2007-07-10
All I can say is that it's never happened here, with any version of Gaim (or pidgin, which is the updated version of Gaim).

One thing you can try is clearing out your Gaim preferences and set up everything again just to see if it works.

From a terminal (Applications->Accessories->Terminal):

**mv ~/.gaim ~/.gaim-bu**

Then run gaim again.  

(If you want your old settings back -- with the possible crash -- type **mv ~/.gaim-bu ~/.gaim** in the terminal.)

---

### Post by Angelus7 on 2007-07-11
I updated Gaim via Automatix...

Works like a charm. =) (Case closed)

---

