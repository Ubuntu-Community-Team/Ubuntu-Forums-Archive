---
title: "The ekiga test call isn't giving me any feedback"
date: 2007-02-22
forum: General Help
---

### Post by billdotson on 2007-02-22
I got a headset and plugged it in.  The automated voice told me that anything I said would be repeated back to me, but I talked for awhile and nothing.  I also tried having the audio plugged in for the headset so I would just hear it on the headset and not the speakers.. but nothing.

Weird thing is though I can hear the dial tone and everything I am just not getting any feedback

---

### Post by drpaul on 2007-02-22
Have you tested your microphone capture with any other software?

Paul

---

### Post by billdotson on 2007-02-22
yes it works in windows and i can hear my voice amplified.  it won't capture in Linux anymore though.  I recorded a couple seconds in sound recorder then quit and deleted that file.  Then I tried to record another and it just auto-mutes all captures.  I can't get it to record with audacity either.  but it definitely did work in Windows.

---

### Post by drpaul on 2007-02-22
If you are using Alsa, use alsamixer to look at the status of your sound channels.  Make sure that the capture channel you are using is not muted and has high amplitude.

If all those are good, then you might install a newer version of the alsa driver. not hard to do. there are lots of threads around that give detailed steps.

HTH

Paul

---

### Post by PurplePenguin on 2007-02-28
> **billdotson said:**
> yes it works in windows and i can hear my voice amplified.  it won't capture in Linux anymore though.  I recorded a couple seconds in sound recorder then quit and deleted that file.  Then I tried to record another and it just auto-mutes all captures.  I can't get it to record with audacity either.  but it definitely did work in Windows.

There are threads all over the forum about this.  A bit of fiddling with mic capture on Alsamixer will fix it. :)  It definitely will work in linux, too, don't worry!

---

### Post by Chili.willy on 2007-08-11
In another thread someone posted a very helpful hint. Type this into a terminal:
[COLOR="SeaGreen"]vumeter -r &[/COLOR]
That gives you a nice visual indicator of your mike input level.

FWIW, these are the Alsa settings that enabled me to record:
Playback tab: Master 50%, PCM 100%, Line-in 100%, CD 60%, Mic 100% (but muted), PC Speaker 100%, Aux 100%. 
Recording tab:both Mic Capture and Capture are at 100%; Mic Capture has the mic symbol muted (but not the speaker symbol). Neither of the Capture symbols is muted. 
Switches tab: Mic Boost is checked. Line-in Capture and Aux Capture are not. 
Options tab: Mic 1 is selected (rather than Mic 2). 
I'm sure some of those settings have nothing to do with making the mike work, but I don't know which ones. 

I tried recording with a phone headset & after lots of fiddling determined that it's not sensitive enough.  A regular microphone works, and so does the builtin laptop mike (but it is subject to lots of noise due to bumps, keystrokes, etc.).

---

