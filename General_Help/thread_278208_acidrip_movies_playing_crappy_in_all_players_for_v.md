---
title: "acidrip movies playing crappy in all players for various reasons"
date: 2006-10-15
forum: General Help
---

### Post by hotani on 2006-10-15
Recently every movie ripped with acidrip will not play in gxine which is my standard player and until recently used for MythVideo. The colors are off - WAY off (greens don't match up with the reds, etc..) - and there is a huge green bar across the top of the video. Audio is fine.

When attempting to open many of these with mplayer, it hangs and dies. I have to kill the process. However, with some movies mplayer is the only thing that will work.

All will have problem-free video in Totem with gstreamer backend, but some are out of sync with the audio. By out of sync with the audio, I mean horribly obviously out of sync. People move their lips to talk, then about a second later the words come out.

Am I doing something wrong, or is this just the poor state of video playback on Ubuntu? I read somewhere that the color problem was a bug in Xine and not acidrip. Not that I care, I just want something to frakking WORK.

It is interesting that mplayer on OS X, in spite of its alpha/beta release status was flawless. I used it for everything, now on Linux it is a steaming pile of poo only used as a last resort.

I have movies I can't watch because they do all of the following: video is trashed in xine, audio is trashed in gstreamer (totem), and when trying to play the file, mplayer goes in the trash.

---

### Post by hotani on 2006-10-16
This has been fixed. Here is the cure: turn off XGL.

gXine is back, mplayer is back. Audio is still frakked in totem/gstreamer but as long as something works i'm happy. I can live without XGL, but since this machine is the TV/Movie player, it kinda needs to have a functional method of video playback.

---

