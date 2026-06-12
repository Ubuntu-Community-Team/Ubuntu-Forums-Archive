---
title: "cron doesn't work"
date: 2007-04-25
forum: General Help
---

### Post by z987k on 2007-04-25
I read through the man page and I thought I got a handle on how to set up a cron job to run every day.

type crontab -e
```
00 06 * * * beep-media-player
```
then save that.

Why doesn't it run?  All I want it to do it run beep-media-player, doesn't have to do anything but open it.

I tried another one 1 minute from when I made it just to test and it doesn't work.

---

### Post by Jussi Kukkonen on 2007-04-25
cron doesn't run in your X session, so it has no idea where it should show the GUI...

The internet probably has an answer to this question (now that you know what the problem is), but you could also just try something like:
```
00 06 * * * DISPLAY=:0.0 beep-media-player
```

---

