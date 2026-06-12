---
title: "Potential Workaround for DVD Burning Problems"
date: 2006-09-17
forum: General Help
---

### Post by Lem on 2006-09-17
I do not wish to make this a HOW-TO just yet, as I have no idea if it works for anyone else, and it's still not an ideal solution.

I have an LG Dual-Layer drive that has burnt CD's successfully from day 1, but refused to even start burning a DVD with gnomebaker,nautilus,nerolinux, bonfire or k3b (Spot the desperation!)

I've now managed to burn a pile of dvd's by doing the following;

NB. Please note that I'm not sure if Step 1 is actually required, so please try it without the growisofs upgrade first and let me know :)

[U]
Step 1[/U]
I upgraded to dvd+rw tools (inc. new growisofs) 6.1-2. 6.1-3 is available and the latest in most repos, but has dependancy issues with a default ubuntu build.
I got 6.1-2 from here;
[http://archive.daniel-baumann.ch/debian/packages/dvd+rw-tools/6.1-2/](http://archive.daniel-baumann.ch/debian/packages/dvd+rw-tools/6.1-2/)

(Double-click the i386 deb file and let GDebi do the rest)

_Step 2_
In k3b select stuff to burn onto dvd, and hit burn. Now change the writing method to DAO and writing speed to 4x (6x didn't work for me despite my drive supporting it). You can save these settings using the 'Save User Defaults' button.

Now burn away! Ok, it's not super-fast and you can't do multisession, but I do at least now get DVDs instead of coasters!

---

### Post by Lem on 2006-09-22
Did this work for anyone?

---

### Post by Monsieur Gonzalez on 2006-09-22
Thanks for the pointer. I was getting slow performances when burning DVD ISO images. Using the updated .deb and changing the growisofs group to burning I can now get 10-12x speed (compared to 4-6 before)

---

### Post by Lem on 2006-09-22
> **Monsieur Gonzalez said:**
> changing the growisofs group to burning 

Can you explain what you mean by this?, as I cannot burn at full speed without failure (but at least I can now burn)

---

### Post by Monsieur Gonzalez on 2006-09-22
Sorry if I didn't make myself clear. There's a "setup wizard" in K3B which changes the 'burning' group privileges for certain programs (cdrecord and so on). I just noticed the growisofs program wasn't changed, and so I manually changed it (sudo chgrp burning /usr/bin/growisofs). Being run with high priority I assume they get more system resources and you can get higher recording speeds.

---

