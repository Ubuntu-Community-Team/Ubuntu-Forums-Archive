---
title: "Disabling Default sound adjustments (EQ)"
date: 2015-09-20
forum: General Help
---

### Post by Nixarter on 2015-09-20
I've noticed that the default sound is modified... the bass and treble are turned up, basically.  This is causing audio distortion and clipping in music and in games I play.  Since this is done at a software level before it gets to the amplifier, volume adjustments are worthless.  This makes certain games, likely the ones recorded near 0dB, unplayable.

The question is actually two-tiered.  It depends on what modifies the sound.  Is it Linux or the sound card/drivers?  In Windows, the audio is muted unless the drivers are installed (naturally).  When installed, the default is the exact same audio distortions added.  I have to manually go into the GUI for the software (Creative Soundcore aka Recon 3Di onboard audio).

I was under the impression that this was processed in the OS, then passed to the soundcard.  I would presume that this cannot run in Linux, thus my assumption was wrong; the processing is done on the soundcard, and must be manually disabled by sending instructions somehow from the OS.  (... unless I'm missing something)

Anyone have experience with this?  Any ides on how to disable this processing?  It isn't quite as annoying as having no sound at all, but often times it is not far off.

---

### Post by Nixarter on 2015-09-20
[ATTACH=CONFIG]264539[/ATTACH]

I was doing some troubleshooting before, and after many hours I figured out that my problem was the channels I wanted to use were muted, so I simply unmuted all channels (see bottom of image).  The "HP Speaker" outputs are the ones that actually output the sound that I need (front/rear headphone jacks).  Some of the others, apparently, were making the unwanted audio adjustments.  So, I went back and muted all but the ones I needed, and the problem is solved.

To do so I ran ```
alsamixer
``` in a normal (non-root) terminal then went left/right with arrow keys and hit the "m" key on all channels that showed numbers (00, which apparently means "unmuted" or "active") to mute them.  I left the two I need unmuted, then hit esc to go back to terminal and then exited.  That fixed all the issues.  :)

---

