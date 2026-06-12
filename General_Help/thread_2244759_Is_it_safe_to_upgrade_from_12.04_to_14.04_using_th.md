---
title: "Is it safe to upgrade from 12.04 to 14.04 using the update manager?"
date: 2014-09-18
forum: General Help
---

### Post by Tom_Carr on 2014-09-18
Is it safe to upgrade from 12.04 to 14.04 using the update manager?
I remember years ago there was some problem with this.  Is it pretty safe now?  Is there a better way?

---

### Post by ibjsb4 on 2014-09-18
This is something that is done every 2 or 4 years.  I think its better to do a fresh install.  There is a big difference in 14.04 and it requires more resources to run.  But if you want to try it, back up your personal files first.

---

### Post by sammiev on 2014-09-18
A fresh install usually seems to run better than an upgrade over a few versions. Any way that you do it, be sure to have your data backed up.

---

### Post by zemega on 2014-09-18
If you don't do any manual installation of programs, manual tweaks, manual scripts, manual config edits, I would say its safe. If you do any, its not safe to do it using the update manager. If you do any, its better to use the terminal, because then you will be able to see what's wrong.

---

### Post by endlessinstant on 2014-09-18
It's safer now than it used to be LOL 

On one of my old machines I ran Software Update from Ibex to Karmic and I probably just got lucky but I never had to reinstall over that time period.   I've since migrated to LTSes and Debian only though so I usually clean install now since new LTSes and Debian versions are slower than the regular Ubuntu cycle.   Be smart with your /home/ data and you don't have to worry so much about blowing up everything else.

---

### Post by Impavidus on 2014-09-19
Release upgrades are quite safe in my experience (8 successes in 8 tries, one machine has been upgraded from Dapper to Trusty, LTS to LTS). It may be a good idea to disable PPAs (I didn't have any) and proprietary drivers (none were available for me). Your system has to be in a reasonably clean state. You can have manually installed software, as long as it is properly separated from the managed software. If you manually compiled and installed software, you may have to recompile it.

---

