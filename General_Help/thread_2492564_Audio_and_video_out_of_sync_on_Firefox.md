---
title: "Audio and video out of sync on Firefox"
date: 2023-11-15
forum: General Help
---

### Post by Autodave on 2023-11-15
This has been an ongoing thing for a few years now.  It happens on Xubuntu, Linux Mint, and Win11.  I'll be watching a podcast and slowly the audio will start lagging behind the video.  When it gets too out of sync, I usually do an F5 and restart it.  It may go a few minutes before it starts to get out of sync again.  Also during this time, you hear short breaks or pauses in the audio.

Not sure how I discovered this last night, but I found that when it gets out of sync, quickly using the icon on the podcast to stop the audio and then hitting again to start the audio, I am back in sync again!  (Much better than F5, but I still wonder if there is anything that I can do to eliminate this.

This does not happen on anything except Firefox.  While I was watching the podcast, I also had the Penguins hockey game on my other screen and it was perfectly fine.  Also, this does not happen on all podcasts.

Thanks!

---

### Post by SeijiSensei on 2023-11-15
Is it also a problem with Google Chrome or the open Chromium browser?

---

### Post by TheFu on 2023-11-15
Podcasts have video?  Thought they were audio only.  I don't use firefox for audio or video.  There are some drastic changes coming in FF that will make it not work for me much longer, if they do what they announced a few days ago related to Wayland-only support on Linux.

I listen to podcasts "offline", without any internet, often when hiking on a trail I know very well. Keeps me from being bored for the 200th time on that trail to hear something new.  The files are saved locally on my player.

You'll need to look at the stream and container to see how they put it together.  If they do hundreds of chunks like an huge list of m3u8 parts, there isn't much besides pre-downloading it into a single file. If they change video resolutions like often happens with commercial m3u8 streams (like on PlutoTV), any player based on ffmpeg will have issues due to the EXT-X-DISCONTINUITY problem. Basically, the different segments don't all have the same frame rates or audio rates.

---

### Post by Autodave on 2023-11-15
I am watching this live.  Watching a recorded one also gives me the same issue.  There is no change in camera.....one camera, no zooming or anything.

---

### Post by TheFu on 2023-11-15
> **Autodave said:**
> I am watching this live.  Watching a recorded one also gives me the same issue.  There is no change in camera.....one camera, no zooming or anything.

What does mediainfo show about the downloaded media file?  Which codecs and container?  Are the audio and video the exact same length?  If you force them to be the same length, does that help?

Maybe if your record it yourself? Then you can control the muxing of the audio and video?

---

