---
title: "High-pitched sound when no other sound playing"
date: 2017-04-30
forum: General Help
---

### Post by fizikz on 2017-04-30
For years I've had the same problem as described in this thread: [https://ubuntuforums.org/showthread.php?t=1213205](https://ubuntuforums.org/showthread.php?t=1213205)

> The problem:
- A quiet, high-pitched squeal that is present whenever the computer is not playing sounds or not muted.

Details about symptoms:
- Playing a sound file (any source) eliminates the noise while the sound is playing. Stopping the sound will usually make it return, but often at a different pitch and volume level.
- The sound file is not simply hiding the high pitched noise, as you can actually hear the noise cut in and out as the sound file starts and stops.
- The noise is in stereo: sometimes it is only on the left speaker, sometimes it is only on the right speaker.
- Muting the volume control eliminates the noise while muted, but if un-muted, the noise is still there at the same pitch and intensity as before.
- If I change the volume control in Ubuntu, the pitch of the noise changes randomly, and it disappears in some of the spots on the volume control... until a sound is played and stopped.
- The noise is not being contributed by my speakers, as it also present when using headphones.

I've had no success trying suggested solutions like:
> 1) Open up (using root) /usr/lib/pm-utils/power.d/intel-audio-powersave

2) Replace or comment out the line:

INTEL_AUDIO_POWERSAVE=${INTEL_AUDIO_POWERSAVE:-true}

3) In its place put the line:

INTEL_AUDIO_POWERSAVE=false

4) Reboot
From: [https://thelinuxexperiment.com/fix-annoying-high-pitched-sound/](https://thelinuxexperiment.com/fix-annoying-high-pitched-sound/)

and also tried combining with commenting out "load-module module-suspend-on-idle" in /etc/pulse/default.pa as suggested [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201?comments=all"). Clearly the issue has persisted over many years and Ubuntu releases, considering it was reported in 2009 and continues to receive comments in 2017.

lspci reports my audio device as Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

This high-pitched noise is really irritating, especially when using headphones!

---

