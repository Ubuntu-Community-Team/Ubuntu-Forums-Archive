---
title: "Kubuntu 18.04 Audio - Strange Behaviour"
date: 2020-11-20
forum: General Help
---

### Post by tobiz on 2020-11-20
I've a new install kubuntu 18.04 on a new machine since Oct 2018, all fixes up to date. I've always had problems with the audio/sound subsystem, it's HDMI connected to a TV. Every thing works as expected except for the audio.  Today I discover this 'strange' behaviour after running Spotify (for the first time). 

When Spotify is configured to be connected to the same machine its running on there is no audio output unless:
1) select Spotify "play" - no sound; 
2) Spotify select "no Play"; 
3) using System Settings app Phonon Audio and Video with "Built-in Audio Digital Stereo (HDMI 2)" selected run "Test", test sound is heard. At the same time then; 
4) with Spotify select "Play", Spotify sound and System Settings test sound both heard; 
5) stop System Settings test sound - Spotify sound continues.  If you now stop Spotify playing and then select Spotify "play" - no sound.  If you repeat the process Spotify sound is restored.  

This behaviour suggests (to me) there is some interaction between 'some' audio apps and the kubuntu 18.04 sound system such that the app sound can only be 'triggered' when the Systems Settings test sound is running.  

This could be a problem with the Spotify s/w or the 18.04 audio, or both.  I've found a similar problem/solution with Zoom.   If I run MythTV V31 there is no such issue, the sound works as it should do. 

If anyone else has had problems with 18.04 audio perhaps they could try the above (after doing all the normal checks: cables, alsamixer, etc., etc).

---

