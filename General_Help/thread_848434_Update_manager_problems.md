---
title: "Update manager problems"
date: 2008-07-03
forum: General Help
---

### Post by itscharles on 2008-07-03
Hey guys,

So ubuntu seems to have this problem where if you are running an update and your computer freezes, well, let's just say it's not fun to fix.

Upon restarting after the freeze/crash, my videocard drivers don't work (640x480 FTL) and I can't run an update.  If I try to update anything, I get:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Ok no problem.  So to fix that, cd /var/lib/dpkg/updates, rm *, apt-get update.  That problem is solved, however, if I run any of the following:
apt-get --reinstall install locales
apt-get -f install
apt-get upgrade
it gets to:

Setting up language-support-writing-en (1:8.04+20080630)...
Generating locales...
  en_AU.UTF-8...  up-to-date
  en_BW.UTF-8...  <system crash/freeze>

If i go into add/remove and try and reinstall my videodrivers, the update hangs on en_BW.UTF-8 and the only way I can get out of it is by restarting my computer.  Sometimes it will say that there is a segmentation fault in en_BW.UTF-8.

Any ideas on how to fix this?  I'm going on vacation this weekend in a few hours but I will have access to this thread while im gone so I can keep checking it.

Thanks!

---

### Post by drs305 on 2008-07-03
> **itscharles said:**
> Any ideas on how to fix this?  I'm going on vacation this weekend in a few hours but I will have access to this thread while im gone so I can keep checking it.

Thanks!

Try going into System, Language Support and unchecking the entry causing the problems. You could also try editing /etc/locale.nopurge and comment out en_BW.UTF-8. It won't try to save it and may eliminate the error.

Once things are restored you could try adding it back.

---

### Post by itscharles on 2008-07-03
> **drs305 said:**
> Try going into System, Language Support and unchecking the entry causing the problems. You could also try editing /etc/locale.nopurge and comment out en_BW.UTF-8. It won't try to save it and may eliminate the error.

Once things are restored you could try adding it back.

Only english is checked in Language Support.

/etc/locale.nopurge doesn't exist, but locale.alias and locale.alias.dpkg-new do, however en_BW.UTF-8(or anything like it) is no where in there.

:confused:

---

### Post by drs305 on 2008-07-03
> **itscharles said:**
> Only english is checked in Language Support.

/etc/locale.nopurge doesn't exist, but locale.alias and locale.alias.dpkg-new do, however en_BW.UTF-8(or anything like it) is no where in there.

:confused:

etc/locale.purge is probably associated with an app named localepurge which eliminates extra language packs that aren't installed. 

You could install it. The first time you run it you select the languages for apt to keep after an install. 

en_BW is one of the choices, so if you just selected the other one you use it might ignore the en_BW package during an install/post-install. Worth looking at.

To install:
```
sudo aptitude install localepurge
```

To run:
```
localepurge
```

I suppose you could also try reinstalling your language pack via synaptic.

---

### Post by itscharles on 2008-07-03
So i install localepurge and it runs so i select the languages i want to keep then it goes through the rest of the installation and gets to...

Setting up language-support-writing-en (1:8.04+20080630)...
Generating locales...
en_AU.UTF-8... up-to-date
en_BW.UTF-8... <system crash/freeze>
so i reboot my comp and run localepurge:
/usr/sbin/localepurge: 85: cannot create /var/cache/localepurge/localelist-new: Permission denied

so i sudo it and i get:
Some new locales have appeared on your system:

be@latin co dv haw kok md ps sr@Latn sw syr wal 

They will not be touched until you reconfigure localepurge
with the following command:

    dpkg-reconfigure localepurge

I run that command and get:
/usr/sbin/dpkg-reconfigure: localepurge is broken or not fully installed

if I try to remove it, the computer crashes because it gets to the setting up language...etc.  Does the same thing if i reinstall.

It does the same thing if i go through synaptic.

This is really getting frustrating and not a good way to start a vacation :mad:

---

### Post by drs305 on 2008-07-03
Did you *select* en_BW in localepurge? My thought was to NOT select it in hopes it would be purged. I'll give it some thought on other options.

---

### Post by itscharles on 2008-07-08
fresh install after a clean format and its doing it again.

GG

---

