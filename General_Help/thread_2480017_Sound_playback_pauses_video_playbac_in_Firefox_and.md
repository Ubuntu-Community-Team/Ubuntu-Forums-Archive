---
title: "Sound playback pauses video playbac in Firefox and Celluloid after upgrading to 22.04"
date: 2022-10-16
forum: General Help
---

### Post by lediableboiteux on 2022-10-16
I just upgraded from 21.10 to 22.04 and had two problems.

The first one was that I had no audio playback in the OS. I fixed this by following the last answer to this question: [https://askubuntu.com/questions/1423121/no-sound-in-ubuntu-22-04-1-lts-after-upgrading-from-20-04-lts](https://askubuntu.com/questions/1423121/no-sound-in-ubuntu-22-04-1-lts-after-upgrading-from-20-04-lts).

This didn&#8217;t fix my second problem, though.

When I try playing video (YouTube, Twitch) in Firefox, it plays a frame and then stops. You can fast forward and rewind the video, but it won&#8217;t play anything beyond one frame or so. BUT! if you mute the sound (either by muting the tab, or by using the &#8220;mute&#8221; button in YouTube/Twitch player), the video plays just fine. There is a similar issue with Celluloid, the difference is that videos would play only a frame muted or not.

Video playback in Steam, Epiphany and Chrome works fine (with sound). VLC and Totem play videos, but there is no sound.

Another weird thing I noticed is that now video thumbnailer in Nautilus fails to create thumbnails for video files.

I have (re)installed ubuntu-restricted-extras, ffmpeg, avcodec, gstreamer. I tried googling, but didn&#8217;t find anything relevant. Needless to say, any of the issues I mentioned were present before the upgrade. Do you have any ideas?

EDIT: I forgot to add one relevant fact: I have purged all snaps, removed snapd and installed Firefox as a deb through Mozilla&#8217;s PPA.

EDIT2: I tried playing just sound on Firefox (specifically by playing audiobook samples on the web) and it works fine. Celluloid plays mp3 files just fine too.

EDIT3: Strange. A random video on a local newspaper&#8217;s page just played without problems (i.e. with sound), so this means it is a problem with specific content type. I&#8217;d gladly provide more info, but I just don&#8217;t know where to go next.

---

