---
title: "HAL/dbus not starting in correct order, help?"
date: 2008-03-26
forum: General Help
---

### Post by el_ricardo on 2008-03-26
To speed up my boot, I edited my /etc/init.d/rc and changed concurrency to "shell". As i'm sure a lot of you know, this screws up HAL! When i get to my gnome desktop, I'm confronted with the "internal error: HAL failed to initialize"

I've looked around on t'internet, and on the forums, and came across [this thread]("http://ubuntuforums.org/showthread.php?t=690446"), deepclutch, in reply #7, says to use update-rc.d to change the order that dbus and HAL are loaded, I was just wondering how to use this command to do that. update-rc.d --help doesn't seem to give much info on usage .... not to a n00b anyhow

cheers!

---

