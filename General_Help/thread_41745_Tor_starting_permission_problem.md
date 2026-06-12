---
title: "Tor starting permission problem"
date: 2005-06-14
forum: General Help
---

### Post by ephman on 2005-06-14
i'm sure this is a pretty easy fix, but i'm an old school apple freak, and have only been running linux for about week (without any major issues... awesome!).  but i'm having a problem starting up Tor:

root@wintermute:/home/ephman # sudo /etc/init.d/tor start
Starting tor daemon: tor...
Jun 14 16:15:06.961 [notice] tor_init(): Tor v0.0.9.9. This is experimental software. Do not rely on it for strong anonymity.
Jun 14 16:15:06.962 [warn] /var/lib/tor is not owned by this UID (115). You must fix this to proceed.
Jun 14 16:15:06.962 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jun 14 16:15:06.962 [err] init_from_config(): Acting on config options left us in a broken state. Dying.


any help would be really appreciated.  i did some searching but can't seem to find this problem.

thank you,
ephman

---

### Post by skoal on 2005-06-14
I don't have this app (daemon) installed but I looked through my /etc/passwd file and don't see any daemon owning that UID, so it must be something updated after that install?  Anyways, if you see that UID owned by "tord(?)" (or the like), check that the path /var/lib/tor is owned by tor (115) and not root.  That's the only thing I can figure from the log file output.  You might want to check and see if there's an /etc/tor directory with a '??.conf' file in there which you might need to set.

\\//_

---

### Post by AndEat on 2005-06-19
[QUOTE=ephman]i'm sure this is a pretty easy fix, but i'm an old school apple freak, and have only been running linux for about week (without any major issues... awesome!).  but i'm having a problem starting up Tor:

root@wintermute:/home/ephman # sudo /etc/init.d/tor start
Starting tor daemon: tor...
Jun 14 16:15:06.961 [notice] tor_init(): Tor v0.0.9.9. This is experimental software. Do not rely on it for strong anonymity.
Jun 14 16:15:06.962 [warn] /var/lib/tor is not owned by this UID (115). You must fix this to proceed.
Jun 14 16:15:06.962 [err] options_act(): Couldn't access/create private data directory /var/lib/tor
Jun 14 16:15:06.962 [err] init_from_config(): Acting on config options left us in a broken state. Dying.


any help would be really appreciated.  i did some searching but can't seem to find this problem.

thank you,
ephman[/QUOTE]



I was having the exact same problem.

Try running 
# sudo /etc/init.d/tor start
and, check here for more info:  [http://www.ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://www.ubuntuforums.org/showthread.php?t=10825&highlight=tor)
luck,

---

