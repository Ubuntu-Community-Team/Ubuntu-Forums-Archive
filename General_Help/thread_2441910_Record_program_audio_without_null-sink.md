---
title: "Record program audio without null-sink"
date: 2020-04-27
forum: General Help
---

### Post by zipdox on 2020-04-27
I want to record audio output from a single application. I know I can do this by creating a null-sink and recording the monitor but is there a way to record application audio without having to set up a virtual sink and loopback?

---

### Post by TheFu on 2020-04-27
**ffmpeg** can record from the device.  Lots of other tools can do that too.  simplescreenrecorder can do it too.  Just set the video bitrate to be 1 fps for the recording, then you can remove the video after pretty easily to have just the audio left.  vlc is another option, though i find it very clunky compared to a tiny ffmpeg command.

---

