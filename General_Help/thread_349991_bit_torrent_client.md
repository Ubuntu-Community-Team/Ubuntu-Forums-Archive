---
title: "bit torrent client?"
date: 2007-01-31
forum: General Help
---

### Post by cptjaben on 2007-01-31
I'm having problems with azureus lately on my desktop, it seems that if i turn off my computer or log out without closing the program that it refuses to run upon restarting my computer. Anyway, I'm wondering what some good alternative clients are that have simlar features. also, if someone would care to take a stab at fixing azurues that would be most appreciated. 

Thanks much.

---

### Post by taurus on 2007-01-31
There are a few other options that you can check out or play with:  bittornado, deluge, rtorrent (terminal), ktorrent (KDE), and transmission.

---

### Post by FluffyElmo on 2007-01-31
Azureus has been pretty erratic for me lately as well. The last update had a note strongly suggesting an upgrade to Sun JVM1.5.0_10 as it fixes a memory leak bug that azureus suffers from. You may want to try that before anything else.

---

### Post by Kateikyoushi on 2007-01-31
I tried some in my opinion the best client is rtorrent, I have no problem with the terminal in fact I prefer it but if only it had a gui could take on the world.

---

### Post by bionnaki on 2007-01-31
the best gui client handsdown is ktorrent - runs exactly like utorrent. I recommend 2.1rc1 found here: [http://ktorrent.org/index.php?page=downloads](http://ktorrent.org/index.php?page=downloads)

dont be afraid of running kde apps on gnome - works great.

azureus is a huge resource hog on the other hand...

---

### Post by cptjaben on 2007-01-31
ktorrent looks awesome, thanks for the advice everyone, if ktorrent doesn't work out i think i might try that java update. Thanks much

---

### Post by drumkitcat on 2007-02-01
> **bionnaki said:**
> the best gui client handsdown is ktorrent - runs exactly like utorrent. I recommend 2.1rc1 found here: [http://ktorrent.org/index.php?page=downloads](http://ktorrent.org/index.php?page=downloads)

dont be afraid of running kde apps on gnome - works great.

azureus is a huge resource hog on the other hand...

Sorry, I'm new to this... are you saying that ktorrent will run on ubuntu? Or do you need to be running kubuntu?

---

### Post by Maestro23 on 2007-02-01
> **drumkitcat said:**
> Sorry, I'm new to this... are you saying that ktorrent will run on ubuntu? Or do you need to be running kubuntu?

Should work fine. I'm running Ktorrent on Xubuntu with no problems at all.  Give it a try.

---

### Post by PetePete on 2007-02-01
you can run KDE apps, just got to make sure u've got the KDE librarys. .... but using app-get etc this will install the librarys required for you... so you mgiht notice a rather large download the first time you get a kde app!

---

### Post by stoeptegel on 2007-02-03
> **taurus said:**
> ..., and transmission.

What makes transmission a lesser nice client is that it does not listen to the trackers supplied announce interval. In fact, it does not even follow the standard of 30 minutes on normal usage. It also keeps hammering peers in swarm every some seconds when it is seeding a torrent, even if the other peer is also a seeder.
(some people also call this tracker abuse and ignoring the protocol specifications)


Not that this makes it an evil client, as i also want to respect the work of the devs there... but i like to point out as a biased bittorrent user, that there are clients out there who have a better behaviour.

---

### Post by Tim T on 2007-02-03
> **FluffyElmo said:**
> Azureus has been pretty erratic for me lately as well. The last update had a note strongly suggesting an upgrade to Sun JVM1.5.0_10 as it fixes a memory leak bug that azureus suffers from. You may want to try that before anything else.

how would i go about installing the java update? i keep getting errors and think that might help.

---

