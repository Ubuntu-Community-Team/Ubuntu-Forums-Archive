---
title: "Beagle locks up on Matlab Files"
date: 2006-11-12
forum: General Help
---

### Post by FryerFox on 2006-11-12
I have noticed that Beagle (Desktop Search) occassionally locks up when trying to index Matlab files. beagled-helper occassionally goes to 100% CPU useage and gets stuck as described in this Bugzilla report:

[http://bugzilla.gnome.org/show_bug.cgi?id=348139]("http://bugzilla.gnome.org/show_bug.cgi?id=348139")

It is reported closed, and should be fixed in recent versions of Beagle, but not the one currently in the repositories (0.2.9).

In any event, I just wanted to let others know about this bug since I couldn't figure out why it was crashing at first so I had to exclude *.m from the indexing: System->Preferences->Search & Indexing->Indexing->Exclude *.m files.

---

