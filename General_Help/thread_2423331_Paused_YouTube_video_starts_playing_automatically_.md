---
title: "Paused YouTube video starts playing automatically on resume from suspend"
date: 2019-07-21
forum: General Help
---

### Post by kent-3 on 2019-07-21
Ubuntu Studio 18.04.2, KDE Desktop, Chromium 75.0.3770.90

A very weird problem that just started happening: 

If a YouTube video is open in Chromium and paused, on resume from suspend it will start playing, even before I log in (and then I have to find what window/tab it is to stop it). What actually seems to be happening is that the YouTube video starts playing when the system enters the suspend sequence, and is continuing to play on resume. Regardless, I don't know what is triggering it to start playing. I have no keyboard shortcuts setup, and it occurs even by closing the laptop lid (my usual method for suspending). It only seems to happen in Chromium -- not Firefox. If more than one YouTube video is open in a tab, it starts playing the last played video. 

I did recently make a change to KDE Plasma settings to remove the "now playing" media status from the login screen, but there were also a bunch of system updates recently installed, so I can't tell what caused this problem.

Any insight appreciated!

---

### Post by CatKiller on 2019-07-21
[Someone else had the same issue](https://ubuntuforums.org/showthread.php?t=2422480). Their solution may work for you, too.

---

### Post by kent-3 on 2019-07-21
> **CatKiller said:**
> [Someone else had the same issue]("https://ubuntuforums.org/showthread.php?t=2422480"). Their solution may work for you, too.

That was it! Thank you very much.

For the sake of posterity: the solution was go into Advanced Power Management Settings and uncheck "Pause media players when suspending". I never altered that setting before so I'm guessing this is a bug that came about because of recent system updates.

---

### Post by jradinger on 2019-09-12
> **kent-3 said:**
> the solution was go into Advanced Power Management Settings and uncheck "Pause media players when suspending".

I also have the same problem that youtube videos start when opening the lid (or resume from suspend in general) but on Ubuntu Budgie 18.04.3 LTS. This is especially annoying when my laptop gets awake from suspend (even when the lid is closed -> issue of the [unreliable S2idle suspend mode]("https://askubuntu.com/questions/1115572/ubuntu-18-04-dell-xps15-9570-impossible-to-reliably-suspend-hibernate"); S3 suspend is not officially supported in the new [Dell XPS 15 7590]("https://www.notebookcheck.net/XPS-15-7590-No-DPC-latency-issues-but-75-C-throttling-and-no-S3-sleep.426999.0.html")) and youtube starts playing. Unfortunately, there is no check "Pause media players when suspending" in Ubuntu Budgie....how can this be solved on platforms other than KDE?

Dell XPS 15 7590
Ubuntu Budgie 18.04.3
Chrome Version 77.0.3865.75 (Official Build) (64-bit)

---

