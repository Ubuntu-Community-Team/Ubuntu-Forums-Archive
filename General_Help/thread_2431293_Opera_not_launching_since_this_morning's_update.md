---
title: "Opera not launching since this morning's update"
date: 2019-11-14
forum: General Help
---

### Post by Buntu Bunny on 2019-11-14
Opera version 65.0.3467.38 (downloaded from Software Centre)
Latest update 11/14/2019

```
buntubunny@buntubunny-Inspiron-3650:~$ opera
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-28-1804
snap connect opera:gnome-3-28-1804 gnome-3-28-1804

buntubunny@buntubunny-Inspiron-3650:~$ snap install gnome-3-28-1804
snap "gnome-3-28-1804" is already installed, see 'snap help refresh'
buntubunny@buntubunny-Inspiron-3650:~$ snap connect opera:gnome-3-28-1804 gnome-3-28-1804
buntubunny@buntubunny-Inspiron-3650:~$ opera
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-28-1804
snap connect opera:gnome-3-28-1804 gnome-3-28-1804
```

I looked at 'snap help refresh,' but didn't see how any of the options applied to my problem. 

Suggestions?

---

### Post by crip720 on 2019-11-14
Don't know much about snaps, but figure a remove and reinstall of opera might help.  Opera also has a regular deb version you could try.

---

### Post by Frogs Hair on 2019-11-14
I also use the .deb from the Opera site which updates with the system.

---

### Post by nataly2 on 2019-11-14
I have the same problem. Reinstall (remove and install) opera via snap doesn't help

---

### Post by crip720 on 2019-11-14
Would suggest of removing snap opera and replacing with .deb opera.  Think it is listed in software store below the snap version.

---

### Post by vkotynek on 2019-11-14
I've also experienced this bug today. Uninstalling Opera and re-installing from .deb downloaded from opera.com helped. Re-instaling from Ubuntu Software didn't.

---

### Post by Buntu Bunny on 2019-11-14
Well, I came back from running errands and Opera started with the click of the icon. I did nothing, so I have no idea what the problem was. I probably should install the .deb version though. Software Centre rarely has the most recent versions.

---

### Post by Frogs Hair on 2019-11-14
> **Buntu Bunny said:**
> Well, I came back from running errands and Opera started with the click of the icon. I did nothing, so I have no idea what the problem was. I probably should install the .deb version though. Software Centre rarely has the most recent versions.

Opera from .deb updated this morning 
Version:65.0.3467.38
Opera is up to date

---

### Post by Kurt_Alan on 2019-11-14
Ditto, same problem after update. I uninstalled from the GUI, then re-installed via CLI. Now it opens. When I re-installed via GUI, it failed.

---

### Post by Buntu Bunny on 2019-11-14
> **Frogs Hair said:**
> Opera from .deb updated this morning 
Version:65.0.3467.38
Opera is up to date

Interesting. That's the same version I now have which means that Software Centre is offering the same version. I always assumed that the Ubuntu versions were usually less up-to-date. Apparently not so here. I'm also guessing that I probably would have still had the same self-correcting problem. 

> **Kurt_Alan said:**
> Ditto, same problem after update. I uninstalled from the GUI, then re-installed via CLI. Now it opens. When I re-installed via GUI, it failed.

So apparently, there are still problems.

---

### Post by pe83 on 2019-11-15
Same problem here couldn't find the solution yet. Does anyone now how to repot this to opera devs ?

version 64.0.3417.92
updated 14/11/19

---

### Post by Buntu Bunny on 2019-11-15
> **pe83 said:**
> Same problem here couldn't find the solution yet. Does anyone now how to repot this to opera devs ?

version 64.0.3417.92
updated 14/11/19

pe83, welcome to the Ubuntu Forums! Try the [Opera Bug Report Wizard]("https://help.opera.com/en/computer-bug-wizard/").

---

### Post by nataly2 on 2019-11-16
The bug has already fixed. Try to refresh Opera via snap. I did it and it works fine. I contacted to Opera support and explained them this problem. They updated Opera snap version to 64.0.3417.92

---

