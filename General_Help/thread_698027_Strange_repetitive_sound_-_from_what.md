---
title: "Strange repetitive sound - from what?"
date: 2008-02-15
forum: General Help
---

### Post by justmark on 2008-02-15
Love my Ubuntu! It just works, which is great.

But, every once in awhile, my computer makes a strange sound / tone, 3 notes up, then 3 notes down. 1, 2, 3, 3, 2, 1... I'm no music major, but the frequency is somewhat low, but not bass, if that makes any sense. Very pleasant, just strange because I don't know what's causing it.

It doesn't happen with any regularity that I can tell. It doesn't happen at any particular time of day. Doesn't seem to matter what I'm doing, or even if I'm doing anything at all... I've just been sitting in front of the glass and the tones play. No dialogs pop up. No running program needs attention. Nothing in /var/log/messages (or any log that I can tell).

Any clues?

Thank you

---

### Post by pointone on 2008-02-16
If you're running Pidgin / Gaim / aMSN / some other chat program, it may be configured to play a sound when someone logs in / out.

---

### Post by justmark on 2008-02-17
That could be it, I run pidgen every once in awhile. I guess I never correlated that. I don't do IM often, so sometimes it just sits docked in the panel... 

Thanks!

---

### Post by Crafty Kisses on 2008-02-17
> **justmark said:**
> That could be it, I run pidgen every once in awhile. I guess I never correlated that. I don't do IM often, so sometimes it just sits docked in the panel... 

Thanks!

If Pidgin is not the source of the sound, you can go into your terminal and type the following ```
beep
``` Then you can see if it sounds like that.

---

### Post by justmark on 2008-02-19
I found that Pidgin was setup for a 3-tone sound for a buddy sign on, and another 3-tone sound for when a buddy signed off.

I watched my buddy list as best I could, and found that a particular buddy was periodically signing off, then right back on... seems his Treo was losing signal every so often when he drove... ;)

I'm not 100% convinced it was always him, but that sympton sure does nail it.

---

### Post by TheOrangePeanut on 2008-02-19
I posted this same question in around Octobe when I first installed Ubuntu.  It was Pidgin then too.  Haha

---

