---
title: "Mozilla Sound playback stop before end of file"
date: 2007-12-12
forum: General Help
---

### Post by ridgeland on 2007-12-12
Not in 7.04, only in 7.10. Thunderbird and Firebox problem only? XMMS is OK
I first saw this in Thunderbird.  My new email announcement played only 80% of the WAV file.  I guessed the problem was the new Thunderbird 2.0.0.8 so I removed it and installed 1.5.0.13 from Ubuntu 7.04.  Same problem the sound file gets cut short.
So I searched the forum.  I found a sound file in a thread here:
[http://ubuntuforums.org/showthread.php?t=630336&highlight=thunderbird+sound](http://ubuntuforums.org/showthread.php?t=630336&highlight=thunderbird+sound)
NT4usB posted his preferred email announce WAV file.  Clicking on it I get the same problem.  It should play "zing...message for you sir" but all I hear is "zing...message for y"
I saved NT4usB's WAV to my local drive.  Then I opened the local copy and it played completely.  (XMMS is my default player).
The error is in both Thunderbird and Firefox.  Mozilla only?  Haven't seen it outside Mozilla.
I tried options in Menu -> System -> Preferences -> Sound  I'm using ALSA for everything there, but it doesn't seem to matter.  I looked in about:config in both Firefox and Thunderbird but did not see anything I thought was a solution.
Any suggestions?

---

### Post by jon.carstens on 2007-12-14
I've got exactly the same problem. The file plays fine in Totem, but wont finish in Thunderbird.

---

### Post by ridgeland on 2008-03-11
I installed Ubuntu 8.04 Alpha 6 yesterday.
This problem is solved in 8.04.   Whatever 7.10 broke 8.04a6 fixed.

---

