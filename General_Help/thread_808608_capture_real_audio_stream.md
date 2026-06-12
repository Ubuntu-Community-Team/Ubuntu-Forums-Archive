---
title: "capture real audio stream"
date: 2008-05-26
forum: General Help
---

### Post by evaristegalois on 2008-05-26
I can capture an internet audio stream (public radio for example) with the command

> mplayer -noframedrop -dumpfile ./quirks-and-quarks.ram -dumpstream mms://wm.cbc.ca/cbcr1-ottawa

and then use cron to create timed recordings. It occurred to me that it would be nice to do this with one java or perl program, not using mplayer. Is there a way to capture an audio stream with program-internal commands, for example open a file writer in java and adding the stream data to the file for a given period of time?

---

### Post by Bubba64 on 2008-05-26
[QUOTE=evaristegalois;5049650]I can capture an internet audio stream (public radio for example) with the command



and then use cron to create timed recordings. It occurred to me that it would be nice to do this with one java or perl program, not using mplayer. Is there a way to capture an audio stream with program-internal commands, for example open a file writer in java and adding the stream data to the file for a given period of time?[/QUOTE

I sometimes use sound recorder in sound-video in applications for live recording, but it can Be hard to get working. Download helper from Mozilla add ons is a good way of capturing audio and audio visual stuff,
[https://addons.mozilla.org/en-US/firefox/search?q=%20download%20helper](https://addons.mozilla.org/en-US/firefox/search?q=%20download%20helper)
This doesn't answer your java questions but might be of help. There was a post a while back I saw on the forum which explained how to capture internally you will just have to search if that is what you really want.

---

### Post by MrFSL on 2008-05-26
>  It occurred to me that it would be nice to do this with one java or perl program, not using mplayer.

Why re-invent the wheel?

If you have a system that works I would use it. If you wanted to add functionality in scheduling for instance, then sure, a simple Perl/Tk interface could aid in that - but I would stick with mplayer if it works for you.

---

