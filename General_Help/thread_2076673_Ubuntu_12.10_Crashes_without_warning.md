---
title: "Ubuntu 12.10 Crashes without warning"
date: 2012-10-26
forum: General Help
---

### Post by daniel.cotter on 2012-10-26
I am using 12.10, dual booting with 12.04. This is the third day since I did this install. Both fresh installs, 12.04 is two days older, and here is my question:

While using 12.10 just now, it crashed without warning, all the way dead, twice in rapid succession.  Both times, I had RhythmBox running.

Where do I go in the logs to see what caused these crashes.  Which log is it that I can paste relevant entries from, in order to ask for assistance in solving it?

I am wanting to keep 12.10, only because my smart card reader (CAC) worked with minimal setup, whereas extensive attempts under 12.04 have yielded no results.

Thanks in advance...I will paste log entries as soon as I can find them.

Daniel

---

### Post by dino99 on 2012-10-26
the first place to glance at is : ~/.xsession-errors  (ctrl+h to unhide it)
the second is /var/log/*

but you might want to run a ram test first with memtest

---

### Post by daniel.cotter on 2012-10-26
I am trying to post log files, but network problems are preventing the post.  I'll keep trying.

The size of the files has something to do with it, no doubt.

---

### Post by Stearns on 2013-01-26
Having a similar issue with 12.10. It completely crashes after playing music (mediaplayer doesn't matter, happens when using ncmpcpp + mpd, rhythmbox and clementine) for 20+ minutes. Have been having issues locating the specific lines in the errorlogs but will be posting them ASAP.

This issue hasn't been present since day 1 of this installation, though, which is quite odd as I haven't changed anything in that regard since then, other than a changed preference in mediaplayer.

EDIT1: Seems the crash occurs when manually switching tracks.

EDIT2: Downgraded to 12.04, crashing doesn't occur anymore as it seems.

---

