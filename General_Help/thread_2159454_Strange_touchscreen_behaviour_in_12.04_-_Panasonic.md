---
title: "Strange touchscreen behaviour in 12.04 - Panasonic Toughbook CF-19 mk.I"
date: 2013-07-03
forum: General Help
---

### Post by jars121 on 2013-07-03
G'day,

I picked up a Toughbook CF-19 mk,I yesterday, which came with a fresh installation of XP Professional. I avoid Windows at the best of times, and figured 12.04 would be a nice OS for this little unit.

Out of the box, pretty much everything works under 12.04 (as I hoped/expected). I'm having major problems with the touchscreen interface though! On startup, the trackpad and left/right buttons, as well as USB mouse work perfectly. However, if I touch the screen, the left/mouse/USB LMB/RMB are rendered inactive. The trackpad and USB mouse pointer functionality is there, I just can't click.

It's worth mentioning that when touching the screen, the screen registers the touch, and moves the pointer to around 50px from where I touch the screen. However, it too doesn't register a click.

I've tried installing utouch and the xinput-calibrator, but the calibrator utility doesn't register a click when I touch the little white crosshair, and then renders the mouse/trackpad buttons useless, so I'm forced to restart.

I've tried compiling linuxwacom-0.9.7 from sourceforge but to no avail. Comparing the process to the wiki,ubuntu.com/CF-19 page, I'm getting some errors that they aren't...

Does anyone have any ideas here? I can post results from various terminal commands and the error report from the above attempted install, I just don't know what would be helpful/useless at this point, so please let me know!

Thanks!

---

### Post by jars121 on 2013-07-04
Anyone? I haven't had a chance to further my research into this problem today, but I'm hoping someone here has some ideas.

---

### Post by claracc on 2013-07-04
Perhaps, this link: [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen) can be useful for you.

---

### Post by jars121 on 2013-07-04
Thanks for that :)

Everything seems to be working now...

I ran the xinput utility and wrote the required calibration lines into the /etc/X11/ conf file, and it seems to be working fine. I'll restart the system and see what happens.

---

### Post by claracc on 2013-07-05
You are welcome.

If you got fixed your problem, please, mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) in order other users can find the information easily

---

