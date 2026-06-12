---
title: "mozilla firefox talkback agent and disappearing window borders"
date: 2008-06-14
forum: General Help
---

### Post by bluepowder7 on 2008-06-14
ok, i've yet again had the annoying moz firefox talkback agent show it's ugly head after 'fox crashed.  and, not only am i finding it annoying having it, it's hard to close it, and as a bonus it wipes out ALL window borders on all applications - so now i can no longer minimize / close / move any window unless i right-click its entry in the toolbar.

1 - how do i obliterate talkback from ever showing up again?  if firefox has to crash, i'd like it to crash on its own and leave everything else alone.

2 - how do i regain those window borders?  do i need to "killall nautilus" to get it to recycle, or is there a better way?  since i have a video encoding process happening in a terminal window now, will i lose all visibility to its progress and whatever other questions the script is going to ask me later on???

window borders = the thin border line, plus the _, X, and square in the top-right corner of each window.  the "file - edit - view" stuff is still intact.

btw - i have firefox32 as well as firefox64 since i'm on an AMD system.  this crap-out has happened a few times, but i honestly can't say whether it happens on ff32, ff64, or both.

---

### Post by cariboo on 2008-06-15
You can disable the talkback engine in Edit-->Preferences-->Security by unticking the lines that start with **tell me if the site**. As for the title bar problems, I believe it is a bug in compiz. You may have to wait until your video process is finshed, as the only way I've found to fix this problem is to boot into an older kernel and everything seems to be ok. I then boot into the current kernel and the problem is fixed.

Jim

---

### Post by bluepowder7 on 2008-06-15
point 1

hmm, doesn't that only prevent the agent from showing up when there's forged pages?  the agent i was seeing was the one that showed up in new windows after a crash, and was more of the "oh dear, we crashed, let's tell mozilla all about it..."  it usually is nearly impossible to "opt out" of it unless i click 'Next' a few times during the setup and then cancel at the second-last step.  kinda silly, since the first screen says "hey, you can opt out of this" - even though it doesn't LET me opt out at that point.  and it keep repeating it.

anyhoo, i suppose i can sidestep this annoyance by migrating over to Opera, which i like more anyways because it looks 'cleaner' and has mouse gestures that i got accustomed to VERY quickly.  doesn't support flash content, though.  damned 64-bit OS.


point 2

ok, so if the missing windows are a compiz-fusion bug (which apparently i can "solve" by rebooting, though i can reboot into the same kernel), is there a way to check which revision of CF i'm running?  and, should i look at a newer version?  what about migrating to a different "type" of compiz, like that beryl thing?

---

