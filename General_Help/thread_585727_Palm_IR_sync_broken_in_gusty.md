---
title: "Palm IR sync broken in gusty"
date: 2007-10-21
forum: General Help
---

### Post by Devo66 on 2007-10-21
This worked in Feisty.  I have a Palm Vx that I sync via IR to my Acer Travelmate 4000 laptop.  This worked in Dapper, Edgy, and Feisty, but does not work in Gutsy.  This is a fresh install of Gusty, but I kept a copy of my old home folder and etc folder for reference.  I've looked in both those folders and duplicated the configuration on the new machine with no luck.  I had been using j-pilot for the sync, but I've also ran irdadump and got 0 packets received, so it's not communicating.

---

### Post by Devo66 on 2007-10-28
Fixed.  irda-setup service wasn't enabled by default.  Apparently it's needed in addition to irda-utils service, which was enabled by default.

---

