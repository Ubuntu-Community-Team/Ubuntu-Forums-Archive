---
title: "Rhythmbox works in Gnome but not KDE"
date: 2005-04-29
forum: General Help
---

### Post by mduduzi on 2005-04-29
Rhythmbox launches in both KDE and Gnome but cannot play music in KDE.

By chance, I found that it can play in KDE under special conditions.

1. This is repeatable and appears to be independent of which user is logged in
2. When multiple X sessions are running concurrently (using Xnest) Rhythmbox works well in either KDE or Gnome - provided at least one of the sessions is Gnome. When both sessions are KDE, same problem arises.

The exact error messages are:
(i) Dialog box with tittle: Error <2>. Message: Could not open resource for writing.
When I click OK
(ii) Tittle: Error. Message: Could not pause playback.
But all the while it's NOT playing and the status on top says "NotPlaying".

I'm running a fully updated Hoary AMD64 on Gigabyte GA-K8NS Ultra-939. My software environment is Ubuntu + KDE rather than Kubuntu -if that makes any difference. The kernel in the AMD64 generic (due to nvidia-glx).

Perhaps the default sound systems of KDE and Gnome are causing the offense? But sound works just fine in both environments -even concurrently.

Any help would be appreciated.

---

### Post by doclivingston on 2005-04-29
That's a GStreamer error. My guess is that it is trying to use ESD as the output, and when you don't log in to a Gnome session, the daemon isn't running.

Could you run the Multimedia Systems Selector (gstreamer-properties, I don't remember whether it is in the preferences menu by default, or not) from a KDE session, and check two things 1) what the output of the Default Audio Sink is set to and 2) whether it works when you click on "test".

---

### Post by mduduzi on 2005-05-01
Thank you very much, doclivingston. You certainly sent me in the right direction. gstreamer-properties was very useful together with the Control Centre. I suspect there is either a bug or some less than astute interfacing between the Control Centre and the gstreamer.

That is because of the following, repeatable, observations:
1. The current setting that works is: Control Centre-ALSA & gstreamer-OSS.
2. gstreamer will not work unless gstreamer-properties gets started while CC is set to any but not ALSA. When gsreamer properties is running it must be on any but OSS.
3. Set gstreamer to use OSS and test the source. While gstreamer is attempting the test, switch the CC to ALSA and apply the changes. CC might complain, ignore it. gstreamer will proceed with the test. Test the sink -it should also be fine. After closing both CC and gstreamer-properties. All sound will be working fine.


Thanks once again.

---

### Post by doclivingston on 2005-05-01
Okay - I'm fairly sure I know the problem

With OSS only one thing can use the sounds card at once, but with ALSA more than one can.

If ARTS (the kde sound server) is started 2nd it works, becaause things happen in the following order:
1) GStreamer starts using the sound card with OSS (nothing is using the sound card at this point)
2) ARTS starts using it with ALSA, which works because ALSA supports concurrent access

If ARTS is started 1st the following happens:
1) ARTS starts using using the card with ALSA
2) GStreams attempts to use the sound card, but because OSS doesn't support concurrent access and ARTS is using it, it fails.


If you can, set GStreamer to use ALSA as well - I imagine it should then work regardless of which order you start things in. Although similar situations may occur in games if SDL is using OSS.

---

