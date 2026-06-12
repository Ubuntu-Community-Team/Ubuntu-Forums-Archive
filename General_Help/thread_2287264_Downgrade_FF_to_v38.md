---
title: "Downgrade FF to v38"
date: 2015-07-18
forum: General Help
---

### Post by Quarkrad on 2015-07-18
I have two machines running 14.04 that suddenly have started crashing firefox causing a Mozilla Crash Reporter window to open.  I have been 'off air' for a few days so may have missed something on these forums.  I have not found anything (recently) on the web apart from some issues re firefox and youtube. I have followed these posts advice but ff is still crashing each time I use it.  Is it possible to downgrade to a previous version of ff?  If so how is this done?

---

### Post by monkeybrain20122 on 2015-07-18
No and yes. Dowgrading per se is not possible but it is possible to use FF38 instead of FF39 in the meantime.

Just download the tarball for firefox 38 from [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/) (find the firefox version, go inside, choose linux 32b or 64b, choose the language) extract it to your home, make the firefox binary executable and click it to start. It doesn't install in your system, it coexists with FF39 and uses your old profile, so you can use this until your problem with FF39 is sorted.

To trouble shoot FF 39, start with a new profile and see if it still crashes, if it doesn't then it is probably some addons that you have installed. Close Firefox, open the file manager, press ctrl+h to show hidden files. Rename the directory .mozilla to something like .mozilla-bak, now start Firefox. To revert back to old profile, close FF, delete .mozilla and rename .mozilla-bak back to .mozilla

---

### Post by leunam12 on 2015-07-18
I had that problem with Firefox when it upgraded last Saturday; it started crashing like crazy. What I did was: I restored my system from backup to a pre-update state. I used Synaptic to lock Firefox 38; updated the system and then, a couple of days later, I unlocked Firefox and let it update to start troubleshooting my extensions, but to my surprise, after it updated it was fine. Weird!

Somebody suggested Firefox ESR but I didn't try it.

---

### Post by ndstate on 2015-07-28
Firefox is constantly crashing for me also... started about a week ago.

---

