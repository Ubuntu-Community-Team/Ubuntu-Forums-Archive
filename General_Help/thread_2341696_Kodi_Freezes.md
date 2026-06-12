---
title: "Kodi Freezes"
date: 2016-10-30
forum: General Help
---

### Post by z7APXKm on 2016-10-30
Hi,

Running Ubuntu 16.04.1 LTS with a fresh install of Kodi with a MythTV backend (on the same box).  No dodgy repositories (so far as I'm aware).  I'm using a freeview TBS tuner card.

I can get about 10mins out of Kodi before it freezes and I have to reboot (don't even seem to be able to kill it from the terminal).

The last three lines in the debug log file appear to relate to an EPG scrape:

```

20:10:22 T:139759368267520   DEBUG: PVRTimers - UpdateEntries - updated timer 2 on client 95120:15:22 T:139758604891904   DEBUG: EPG - UpdateFromScraper - updating EPG for channel 'Made In Liverpool' from client '951'
20:15:32 T:139758604891904   DEBUG: EPGContainer - UpdateEpgEvents
20:15:32 T:139758604891904   DEBUG: EPGContainer - UpdateEpgEvents - 0 item(s) updated

```

any ideas?

thanks

---

### Post by z7APXKm on 2016-11-01
Removed vlc.  Seems happier...

---

### Post by monkeybrain20122 on 2016-11-01
It is weird but it seems that Kodi freezes if you have other applications opened (may be minimized) But if there is no other applications running it works fine.

---

### Post by z7APXKm on 2016-11-02
Sadly that's not fixed it.  Sometimes it lasts hours, sometimes minutes.  Now I've killed Kodi from the terminal, but it won't go from the desktop without a reboot.

---

### Post by z7APXKm on 2016-11-09
Seems to be a Unity desktop issue.  Gnome desktop doesn't have the same problem for me.

---

### Post by hargitay on 2017-01-19
I have unity with the same issue.
But the previous version of Kodi didn't freeze...

---

