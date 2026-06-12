---
title: "chromium no tab panel on start"
date: 2013-01-14
forum: General Help
---

### Post by DavidSommen on 2013-01-14
Since the latest chromium update my tab panel is gone when I start the program. It appears when I open a new tab via CTRL+T but that is quite annoying, I normally use the button on the tab panel. Is this a bug or a new "feature"?

---

### Post by tornadof3 on 2013-01-14
Yes that has just happened to me too; would be interested in any solution.

---

### Post by rob1408 on 2013-01-14
Same here.  Chrome has the new tab button, Chromium does not.

---

### Post by justen_m on 2013-01-14
Same problem here with the "upgrade" from Chromium 22.X to 23.X. I'm running Ubuntu 12.10. How do I get this bar back? Hopefully somebody has a solution. FWIW, I'll check to see if I have the same problem on Windows. I tried creating a brand new user/profile from scratch, but that doesn't change anything. I'm thinking about skipping right up to Chromium 24.X to see if that fixes the problem.

---

### Post by pqwoerituytrueiwoq on 2013-01-14
open a tab with [Ctrl]+[T]

---

### Post by DavidSommen on 2013-01-15
> **pqwoerituytrueiwoq said:**
> open a tab with [Ctrl]+[T]
That's the workaround I use for now but it's quite annoying.

---

### Post by CaptainMark on 2013-01-15
It cant be a new feature as the current version of google chrome (24) acts as chromium used to, its possible this is something that canonical have done on purpose whilst packaging chromium, it annoys me, the close/maxmize buttons are also slightly chopped when it happens (only if you are using the non-system title bar and border option, a lot of unity users won't have noticed this)

---

### Post by Gaygerbil on 2013-01-16
I thought this was a feature until I figured out this is only happening in the Linux version of Chromium, seems like it might be a bug. 

Ctrl+T is the obvious workaround or having two tabs always open on startup is another, pretty sure if this wasn't a feature though it'll get fixed in the next release so I'd just hold my breathe and have patience. Not a huge deal if you ask me.

---

### Post by bwanamarko on 2013-01-18
I am having he same issue, since latest update on Ubuntu 12.10. I think this is obviously a bug. But I thought I was losing my mind until I found this thread. So thanks! Hopefully it will be fixed pronto.

---

### Post by CaptainMark on 2013-01-19
Also notice you can't attach a tab to a chromium window with only one other open tab now, but you can drag and attach a tab to a chromium window with multiple tabs open

EDIT: Acutally it's not that black and white, it's working in some circumstances but not others, you cant drag a tab from a single tab window to any other window

---

### Post by DavidSommen on 2013-01-20
How is it possible that a version with such a blatantly obvious bug gets released into the wild?

Is it possible to file a bug with chromium?

---

### Post by justen_m on 2013-01-20
No idea how it got released.

I think I am threadcrapping, but I gave up on Chromium and installed Chrome (24.x). It fixed this bug. Yeah, I know, it is a kludge that shouldn't be necessary. Feel free to roll your eyes at me. I spent a couple hours trying to figure out how to reconfig Chromium to not be evil.

Yes, it is a waste of disk space to have both around, but I am hoping Chromium gets fixed. Just for giggles.

---

### Post by CaptainMark on 2013-01-20
I wouldn't go reporting a bug against chromium until you know its definitely chromium at fault, try to find a distro (a non ubuntu-derivitive) with the same version of chromium or newer installed by default and test out a live cd, if the problem is not present, its either an already fixed bug or its Canonicals bad packaging that caused the bug, my gut tells me latter but let's see

---

### Post by g_dwarf on 2013-01-22
This is the bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1099828](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1099828)

There seems to be a patch available.

---

### Post by CaptainMark on 2013-02-03
This bug has been fixed just now. Use your normal update procedure to get Chromium version 24 from the standard ubuntu repos

---

