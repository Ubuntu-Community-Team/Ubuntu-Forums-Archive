---
title: "Diff between current system and regular ubuntu?"
date: 2007-08-05
forum: General Help
---

### Post by dmee on 2007-08-05
Hey there,

Is it possible somehow to see the diff between the current state of my ubuntu and the regular ubuntu installation? I mean the diff between installed software. The reason is -- I wanna get rid of all unnecessary programs I have installed :).

There's the filter called 'Installed' in the Synaptec but it includes all the apps -- not only those I have installed after setting up the ubuntu.

Any idea?

Dmitry

---

### Post by nick_h on 2007-08-05
Have a look in */var/log/dpkg.log* and the other dpkg log files.

---

### Post by dmee on 2007-08-06
The log contains too much information. I need something lighter :)

---

### Post by nick_h on 2007-08-06
Have a look in /var/cache/apt/archives - this will give you the deb files that have been installed. (unless you have deleted files at some point)

---

