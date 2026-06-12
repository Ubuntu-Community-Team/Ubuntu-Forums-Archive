---
title: "Opening/saving streaming video"
date: 2007-03-31
forum: General Help
---

### Post by qpwoeiruty on 2007-03-31
Is there any way to save or watch mdatrtsp:// streams? I've tried mplayer and vlc, but no luck...

---

### Post by FakeOutdoorsman on 2007-03-31
Try dropping the "mdat" from the stream URL and trying that in VLC.  So if your original link is *mdatrtsp://video.server.com/movie.mov* change it to *rtsp://video.server.com/movie.mov*.

---

### Post by qpwoeiruty on 2007-03-31
> **FakeOutdoorsman said:**
> Try dropping the "mdat" from the stream URL and trying that in VLC.  So if your original link is *mdatrtsp://video.server.com/movie.mov* change it to *rtsp://video.server.com/movie.mov*.

I've tried that in both VLC and mplayer.

VLC says:

live555 demuxer error: no data received in 10s, aborting


mplayer says:

rtsp_session: Not a Real server. Server type is 'DSS/5.5 (Build/489.7; Platform/Linux; Release/Darwin; )'.
Stream not seekable!
Initiated "audio/MPEG4-GENERIC" RTP subsession on port 32810
Initiated "video/MP4V-ES" RTP subsession on port 32812

The extension on the video is .mp4

---

### Post by qpwoeiruty on 2007-04-02
Is there anything else I can try?

---

### Post by qpwoeiruty on 2007-04-03
Is this an unusual request?

---

### Post by qpwoeiruty on 2007-04-06
Impossible?

---

### Post by qpwoeiruty on 2007-04-10
Please?

---

### Post by Azakus on 2007-04-10
What's the actual video? I'll see if I can get Mplayer to do it.

---

### Post by qpwoeiruty on 2007-04-19
> **Azakus said:**
> What's the actual video? I'll see if I can get Mplayer to do it.

Sorry for the delay, I had almost given up hope on this thread. Here's the stream:
mdatrtsp://vstream1.acm.org:554/10.1145/siggraph2005/courses6/crs037-5.mp4

---

### Post by qpwoeiruty on 2007-04-25
No one?

---

### Post by qpwoeiruty on 2007-05-02
please??? :(

---

### Post by zhkent on 2007-05-03
I tried opening it in media player and got this message-
The playback of this movie requires a MDATRTSP protocol source plugin which is not installed.
Being new on feisty thats about my limit, trying a link.

---

### Post by qpwoeiruty on 2007-05-03
> **zhkent said:**
> I tried opening it in media player and got this message-
The playback of this movie requires a MDATRTSP protocol source plugin which is not installed.
Being new on feisty thats about my limit, trying a link.

Yeah, that´s what Totem says when trying to open it. Thanks for trying :)

---

### Post by qpwoeiruty on 2007-05-05
:sad:

---

### Post by qpwoeiruty on 2007-05-06
:sad: :sad: :sad:

This question I've been trying to have answered for 5+ weeks...  surely someone knows something around here :-/

---

### Post by riger99 on 2007-08-11
This solution works for flv, and I bet it might work for your video stream too. The funny thing was that it does not need plugins, extensions, software, etc, to do. Try this solution: [The Fast, Simple Way to Save Streaming Website Video]("http://ubuntulinuxhelp.com/the-fast-simple-way-to-save-streaming-website-video/")
I really hope this helps you.

---

### Post by andrew.46 on 2007-09-04
Hi,

 Well it is a very boring movie about Direct X9 shading language :-) You may be a little unhappy that you had a small space between '2005' making it '20 05' plus as has already been pointed out you need to drop the 'mda' bit as well. Anyway I opened it from the command line as follows:

```
mplayer rtsp://vstream1.acm.org:554/10.1145/siggraph2005/courses6/crs037-5.mp4
```

 I did not try other players because I am a CLI sort of guy :-) Mplayer should also be able to save the stream but my experience with this has only been with Real Audio streaming *sound* not video so others may be able to advise you on this. The mplayer man pages can be a little cryptic!

               Andrew

PS Man you are going to kick yourself for that 20 05 thing: it plays perfectly with vlc as well :-)

---

