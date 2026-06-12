---
title: "Recommend avi video trimmer for Lubuntu 20.04 ?"
date: 2020-07-15
forum: General Help
---

### Post by nginmu on 2020-07-15
Would like to chop a portion off the beginning, a chunk out of the middle, and a portion off the end of an avi video file. Could anyone recommend a simple, not too complicated, gui frontend in Lubuntu's standard repos that can do this?

---

### Post by jp734 on 2020-07-15
kdenlive - simple and easy to use

---

### Post by mIk3_08 on 2020-07-15
> **jp734 said:**
> kdenlive - simple and easy to use yes. I agree with jp734. The new kdenlive 20.04.0 is cool.

---

### Post by TheFu on 2020-07-15
The problem with all the GUI tools is they will re-encode the video file, which will result in a loss of quality.  If that quality loss is acceptable, great.

If it isn't, they you need something that understands GOP frames and only cuts at those locations.  I don't know of any GUI which does. Additionally, most will drop any extra subtitle or SRT or ASS tracks during their cutting.  The only tool I've found that retains all the added tracks is mkvmerge.  There is a GUI, but we are expected to enter timecodes for start-end,start-end,start-end points in the source and write to the target file(s).  By the name, the target file must be an mkv container, but mkvs can hold pretty much any video encodings, audio encodings, subtitles, SRTs, text, images, whatever we like.  It is just a different container that is much more flexible. Of course, if the player(s) for these files are really old, then they may not support mkv, so after the fact, you'd want to use ffmpeg to copy the video and audio FROM the mkv into an AVI container. That can be done losslessly.  Pretty soon, you'd want a script to handle this. While I don't use AVI anymore, I do use MKV extensively and often have to pull tracks, add tracks, cut, merge, using the tools.

If you need frame accurate cuts, then re-encoding everything and having that quality loss is required. No way around it.  Something like vidcutter would be worth looking at.  Sadly, the vidcutter programmer is a mouse-centric user and didn't hook up keyboard shortcuts for most common needs - begin-end cutpoints would have been nice.  Also, vidcutter is a snap, so it is constrained to only access files in the HOME directory.  There may be a flatpak, I've used the AppImage a few times, but the lack of keyboard control has been a real problem to me.  I'm embarrassed to say, but I use a paid Windows tool for video editing.  Often, I have it only generate the project file - EDL or VPrj format, then use some scripts that I wrote to actually perform the edits by generating an mkvmerge script and running that. That Windows editor drops all audio and subtitle tracks except the main ones, which I found unacceptable.  If there are 6 different languages, I want to retain all 6 languages.

Sorry for rambling. Hopefully, some of this is useful.

---

### Post by nginmu on 2020-07-15
Thanks for the leads - will get stuck into investigating further :-)

---

