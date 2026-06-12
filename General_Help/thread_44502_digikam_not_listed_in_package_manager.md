---
title: "digikam not listed in package manager"
date: 2005-06-26
forum: General Help
---

### Post by ehalverson on 2005-06-26
i just installed ubuntu for my family to use on the family computer, and i'm new to ubuntu but i'm used to linux (i run gentoo, but i must admit, ubuntu is VERY impressive) but anyways, when i go to the synaptic package manager i can't find digikam anywhere.  i've looked under graphics, tried reloading my package list, searched names, descriptions, google, forums, and everything, but it's nowhere to be found and neither is anyone with the same problem.  please offer any suggestions even if you're not sure, thanks

---

### Post by ehalverson on 2005-06-26
i also don't have flashplayer-mozilla acroread mozilla-acroread and a lof of other things i really need.  apt-get install can't find them either.  any ideas from anyone?

---

### Post by ehalverson on 2005-06-26
ok, so i went snooping around in my config files, and a comment in /etc/apt/sources.list caught my eye, so i uncommented the 2 lines and now most of the things i was looking for are there, but still no acrobat reader

---

### Post by SGC on 2005-06-26
Acrobat reader 7 and the mozilla plugin are in backports repository while version 5 is in ubuntu's multiverse repository, just add this to apt-get's sources file:

```

#Muliverse
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Followed by:

apt-get update
apt-get install acroread mozilla-acroread

---

