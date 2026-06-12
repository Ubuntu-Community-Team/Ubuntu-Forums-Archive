---
title: "Error starting gnome settings daemon"
date: 2006-12-09
forum: General Help
---

### Post by sadscientist on 2006-12-09
Hey,

I just downloaded/installed 500 and some software updates with the updates manager, and when I log in I'm greeted with the error message: There was an error starting gnome settings daemon.

The name org.gnome.SettingsDaemon was not provided by any .service files.

Anyone know what's up?


(I'm using Ubuntu 6.06 lts)

---

### Post by atarax on 2006-12-18
I got the same error message after installing 500ish updated packages, too, so I guess by the same process. I had already broken my install once and reinstalled Ubuntu, then I had avoided breaking it again by avoiding updating any packages related to X (it was a problem with that that messed everything up...) I had  added extra repositories (as per [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)) and did a full update today, though (I assume you did something similar?) and ended up with the same problem as you. I couldn't find much  info about it using Google, A French page ([http://www.linuxpourlesnuls.org/v4/modules.php?name=Forums&file=viewtopic&t=4215](http://www.linuxpourlesnuls.org/v4/modules.php?name=Forums&file=viewtopic&t=4215)) suggested running:
dpkg-reconfigure -a
I tried this and it didn't fix the problem, though. All the other solutions looked so complicated I would have preferred to just reinstall again!
Anyway, I can't find now the page again which suggested just running a complete upgrade, but for me that fixed the problem, updating all the packages including the ones that were held back. Just comment out all the unofficial repositories in  /etc/apt/sources.list then run on the command line:
 sudo apt-get update
 sudo apt-get dist-upgrade

then reboot.
Hope it solves the problem for you too.

btw, Method B here: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_upgrade_from_Hoary_Hedgehog_-.3E_Breezy_Badger_-.3E_Dapper_Drake)
says to use aptitude instead of apt-get. It may be better to follow their instructions in full, but I hadn't seen it at the time, so I used plain apt-get, and it seems to have worked out alright.

---

### Post by atarax on 2006-12-18
Having done a bit more research, I would just point out that I didn't do the upgrade the way you are recommended. (See [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades))

Anyway, as I say, I was expecting to have to reinstall again in any case, so I'm glad the upgrade saved me the work. Luckily I don't seem to have had any problems doing the upgrade with apt-get, but apparently it's not the way to do it.

Also, sorry for not providing an actual answer to the question: I'm not quite sure why the error occurred. It seems (from the few pages on the subject) that it's something to do with dbus e.g. [http://forums.gentoo.org/viewtopic-t-498821.html?sid=d8e98fe4089d75ea677d51ccc67cd51c](http://forums.gentoo.org/viewtopic-t-498821.html?sid=d8e98fe4089d75ea677d51ccc67cd51c) say to check that  /usr/share/dbus-1/services/ contains gnome-vfs-daemon.service and 
org.gnome.SettingsDaemon.service When I checked and mine didn't have either file, though, I tried to find another solution!

---

