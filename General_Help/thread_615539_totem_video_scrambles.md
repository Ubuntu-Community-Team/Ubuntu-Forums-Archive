---
title: "totem video scrambles"
date: 2007-11-17
forum: General Help
---

### Post by kefurd06 on 2007-11-17
totem video output seems to break daily. restarting totem doesn't help. i have to log out and back in to fix the problem. i think it has something to do with cloniz-fusion. any ideas? here's a screenshot:
[http://www.driveway.com/ohlye75357]("http://www.driveway.com/ohlye75357")

---

### Post by porschify on 2007-11-17
It may be a codec problem.  Do you have the proper codecs installed?

---

### Post by kefurd06 on 2007-11-17
yes. sorry, i should have mentioned that it's not just on movies, when it happens it will even screw up goom (totem's visual display for music)

---

### Post by buttari on 2007-11-17
> **kefurd06 said:**
> totem video output seems to break daily. restarting totem doesn't help. i have to log out and back in to fix the problem. i think it has something to do with cloniz-fusion. any ideas? here's a screenshot:
[http://www.driveway.com/ohlye75357]("http://www.driveway.com/ohlye75357")

Hi,
I had a similar problem and I solved it like this:

1) run gstreamer-properties
2) click on the video tab
3) in Plugin select X Window System (No Xv)

alfredo

---

### Post by amidsin on 2007-11-17
Worked like a charm - didn't even had to log out.

Thanks buttari  =D>

You've got to love ubuntuforums.

---

### Post by matthewcraig on 2007-11-17
I cannot get your screenshot to display, in the original threaded message.  Can you describe this problem more?  I may be having this same problem.

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343)

---

### Post by kefurd06 on 2007-11-17
YES thanks for the help. more specifically, this was hosing my video:

video tab > 
Plugin > X Window System (X11/XShm/Xv)

either device under this plugin has a tendency to hose the video or hang my system completely. the other one is fine. problem tends to happen for me when enabling/disabling cloniz-fusioin or if it crashes and restarts itself.

---

### Post by matthewcraig on 2007-11-17
I made this change and it's been working great so far today.  For the record, I was using Ubuntu-recommended everything with no Compiz.

---

### Post by buttari on 2007-11-18
> **amidsin said:**
> Worked like a charm - didn't even had to log out.

Thanks buttari  =D>

You've got to love ubuntuforums.

I'm glad that it worked!

alfredo

---

### Post by matthewcraig on 2007-11-24
The video is much slower now.  I can tell a big difference.

---

