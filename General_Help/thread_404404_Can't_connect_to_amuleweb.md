---
title: "Can't connect to amuleweb"
date: 2007-04-08
forum: General Help
---

### Post by abelthorne on 2007-04-08
Hello,
After having found out that my problems with aMule (eating up 85 % CPU every 5-10 minutes), I tried to use the no-GUI version amuled combined to amuleweb. Although all have been set correctly (I think), I can't manage to use amuleweb.

I first start amuled, which seems to work, then I start amuleweb ang get an error message *"could not create socket on :4711"*. Anyway, if I try to access localhost:4711 in Firefox, I get amuleweb connexion page (which seems to indicate that it runs as expected) but I can't connect at all : I enter my password, click on "login now" but nothing happens and I have the message *"No passwords specified, login impossible!"* displayed on the page.

---

### Post by defaulk on 2007-06-01
I have the same problem and don't know what to do.  I think I've changed every conf file that I could find that relates to amule.  We must be missing one.  Does anyone have any ideas?

---

### Post by abelthorne on 2007-06-01
I managed to solve my problem some time ago with help from someone on the French Ubuntu forum (and not answering back here, sorry).

There are two amule config files that are used by amuleweb : amule.conf and remote.conf (they are in your home/username/.aMule directory). You have to manually add your password (md5sum encoded) to the relevant options. It seems that even when setting the password everywhere through the GUI options there are still missing ones for amuleweb.

After this, amuleweb worked fine for a while, although a few weeks later it started behaving strangely again : since then I cannot connect anymore (no message error, it just logs and gets back to the login page instead of the files page).
Anyway, unless you want to remotely access amule from another computer and your main problem is the standard GUI using all CPU, you can use amuled+amulegui. It is quite similar to the default GUI but doesn't eat up all your CPU power.

---

