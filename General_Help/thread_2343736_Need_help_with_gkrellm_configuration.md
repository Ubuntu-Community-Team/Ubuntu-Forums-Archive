---
title: "Need help with gkrellm configuration"
date: 2016-11-18
forum: General Help
---

### Post by 1clue on 2016-11-18
Hi,

I have something going on where my box just locks up for  about 5 seconds and then reboots.  Nothing in the logs, no dialog, no  kernel panic.

I want to use gkrellm to give visual statistics,  and also want out-of-bounds information (more like anything over 95%) to a log file, flushed  immediately to the disk.

My window is taller than my monitor, I've set fonts smaller than default and it's still not enough. I have 2 monitors.

I'd like to get all the necessary info but I'm not sure how I can do it.

Here are ideas I've had, if anyone can help me set it up:
[LIST=1]
[*]More than one column of graphs. 
[*]Combine  graphs of related information (cpu core load + cpu core temp for  example) on the same graph using different colors or lines 
[*]Two separate instances each containing different information, one per screen. I have 2 monitors. 
[/LIST]

I've removed non-critical hardware from the machine, it still crashes but not as often.

I'd love to hear any ideas.  This is my primary workstation and I use it to make my living.

---

### Post by 1clue on 2016-11-18
I figured it out from the man page and docs.

---

