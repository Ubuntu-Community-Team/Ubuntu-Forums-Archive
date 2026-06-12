---
title: "Rhythmbox stops making rhythm (or any other noise)"
date: 2004-11-18
forum: General Help
---

### Post by wayover13 on 2004-11-18
Wierd sound problems.  The kind that make you throw up your hands and call in the developers.  So I was fiddling with the system last night, trying to play a CD.  Getting no sound, but that wasn't too surprising once I figured out I forgot to plug in the sound cable from the CD to the mobo.  Then I open Rhythmbox and thought "aha, I can copy over the CD to the HD and play it from there so I don't have to reboot to plug in that dangling CD sound cable."  Worked beautifully: the whole thing got re-encoded in ogg and I was able to listen.  Worked so well, I decided to do a second CD, to which I also listened once it was on HD.

Cut to this morning.  Listened to a couple of those freshly re-encoded songs, after which my wife went off to work asking for those PC speakers I've been promising to give her.  So, I unplug the speakers and off she goes with them.

Cut to later in the day.  I decided to hook up a different pair of speakers I have laying around.  When I do and try to play an ogg, I get no sound.  Plugged into the right hole?  Double check, yeah.  Mute got turned on somehow?  No.  Must be a problem with the speakers.  Fiddle with speakers.  To make sure they work, I plug them into the other machine I have here and insert a CD: out comes the anticipated sound (from the second PC).  So, the speakers work.  Plug them back into the first machine for more testing, but it's futile.  No sound from Rhythmbox or totem.  I check system sounds: no system sounds either.  It's getting strange.  I plug the speakers back into the second box, copy over my ogg files and an mp3 from the first box.  I try playing them there using Rhythmbox and totem.  No sound.  I check system sounds: no system sounds here either.

Overview: I can play CD's just fine on the machine that actually has the CD sound cable plugged into the mobo like it should be.  But somehow, all other sound has gotten mysteriously shut off on both machines.  What in the world could be going on here?  I changed nothing on the first machine: all I did was unplug one set of speakers and plug in another.  And this somehow shuts off totem's, rhythmbox's and the system's sound?  And it can't be that the ogg's got corrupted or something: I've tried mp3's copied over from other machines and/or CD's and they also won't play (no sound).  Somehow, part of my sound system just turned itself off, or sound is getting sent to /dev/null instead of those applications or something.  This is just flaky.

Ideas?

---

### Post by ynef on 2004-11-18
Since you've done some extensive testing on your own, have you tried to plug in some headphones or something? There's the off (way, way off) chance that you managed to screw up the sound card with some static or something, or just the hole where the plug goes.

---

### Post by wayover13 on 2004-11-18
Yep.  Tried headphones.  With either headphones or speakers I get sound when playing a CD (on the second machine where the CD sound cable is actually plugged into the mobo).  I get sound with neither headphones nor speakers when trying to listen to music using Rhythmbox, Totem or system sounds on either machine.  I'll have to reboot at some point here and plug in the CD sound cable for the first machine, and I can see at that point if I can at least listen to CD's on it and get some form of sound out of it.  Too many loose ends for a real diagnosis, I suppose.  But I did at least want to see if others here have had anything like this happen.  Looks like there are alot of sound issues in general with Ubuntu, but I've not seen any quite like mine where only playing a CD causes sound to come out of the speakers but no other sound apps work.  And furthermore, while these toher sound apps were working fine on one system, they suddenly stopped working for no apparent reason.  Frustrating cuz without a chain of events leading to the problem, I just have to make wild stabs at a solution.

---

### Post by wayover13 on 2004-11-18
Now it's getting really scary.  I rebooted, and now all system sounds are back and Rhythmbox and Totem play my ogg's/mp3's.  Why is it scary, you ask?  Because, having no idea why it stopped working to begin with, I have no idea why a reboot should affect it.  More than that: having to reboot to get sound working, if this turns into anything but a one-time anomoly, will be a huge pain in the posterior.  Again, this is just plain flakiness.  I can only hope it proves to be a one-time anomoly.

---

### Post by zenwhen on 2004-11-18
The best issues are the ones that fix themselves. :)

---

### Post by noxfu on 2004-11-18
I've been experiencing the same problem recently.  Sometimes, sound will work.  Sometimes, it won't.  I'm not sure what the significance is, yet, but after some time without music, I went to reboot the computer.  When I clicked on the "Log Out" icon, the system sound played.  I canceled out of it and opened up Rhythmbox....it played sound....

---

