---
title: "Multiple RTSP streams at once in VLC? Or perhaps in Firefox or Chrome?"
date: 2012-11-27
forum: General Help
---

### Post by Roasted on 2012-11-27
I'm curious if there's a way I can draw two RTSP streams at once in any sort of application. Reason I ask is I have two IP based security cameras that support H264, MPEG4, and MJPG. I have Motion running in the background (via MJPG stream, unfortunately, as H264/X264 doesn't seem to be supported) but for my live streams I'd like to utilize the H264 stream, which would use RTSP. I can use two instances of VLC, sure, but it's cumbersome and doesn't look as clean. I'd rather have one window that I can full screen via F11 and have the two RTSP streams evenly displayed, sort of like the way multiple cameras look on some CCTV systems when you're viewing their live streams.

Is there a way to do this in either VLC, Firefox, or Chrome? If Chrome or Firefox work I can simply write an HTML/CSS page to pull the two streams in.

Any insight?

---

### Post by toysareforboys on 2013-01-26
> **Roasted said:**
> I'm curious if there's a way I can draw two RTSP streams at once in any sort of application. Reason I ask is I have two IP based security cameras that support H264, MPEG4, and MJPG. I have Motion running in the background (via MJPG stream, unfortunately, as H264/X264 doesn't seem to be supported) but for my live streams I'd like to utilize the H264 stream, which would use RTSP. I can use two instances of VLC, sure, but it's cumbersome and doesn't look as clean. I'd rather have one window that I can full screen via F11 and have the two RTSP streams evenly displayed, sort of like the way multiple cameras look on some CCTV systems when you're viewing their live streams.

Is there a way to do this in either VLC, Firefox, or Chrome? If Chrome or Firefox work I can simply write an HTML/CSS page to pull the two streams in.

Any insight?I realize you might have already figured it out, but because this thread came up first in every google search I did, I figured I would provide the solution.

With VLC you can use "mosaic" to take two input files (or in your case, two input streams) and display them, split screen style: [http://wiki.videolan.org/Mosaic](http://wiki.videolan.org/Mosaic)

In my case, I was looking for VLC to take two input streams and combine them as one (separate audio and video and combine into one stream), which I found out I could do using somewhat unsupported "input-slave". I tried using the following:
vlc rtsp://192.168.1.28:554/ch0_0.h264 --input-slave rtsp://192.168.1.28:554/ch0_3.h264 :sout=#gather{} :sout=#duplicate{dst=display,dst=rtp{dst=127.0.0.1,port=10002,mux=ts}}

But it failed. It connected to and saw the 2nd audio stream, but would only process and transmit the video stream (even using transcode). I ended up using ffmpeg to do it, which combined the streams and streams them flawlessly:

 ffmpeg -i rtsp://192.168.1.28:554/ch0_0.h264 -itsoffset 1.0 -i rtsp://192.168.1.28:554/ch0_3.h264 -crf 30 -preset ultrafast -acodec aac -af volume=2.5 -strict experimental -ar 16000 -ac 1 -b:a 48k –vcodec copy -f rtsp -muxdelay 0.1 rtsp://127.0.0.1:1937/live/myStream
  
-Jamie M.

---

### Post by mk6032 on 2013-04-22
> **toysareforboys said:**
> I ended up using ffmpeg to do it, which combined the streams and streams them flawlessly:

 ffmpeg -i rtsp://192.168.1.28:554/ch0_0.h264 -itsoffset 1.0 -i rtsp://192.168.1.28:554/ch0_3.h264 -crf 30 -preset ultrafast -acodec aac -af volume=2.5 -strict experimental -ar 16000 -ac 1 -b:a 48k –vcodec copy -f rtsp -muxdelay 0.1 rtsp://127.0.0.1:1937/live/myStream
  



Thanks for posting this. What does your ffserver.conf look like for the rtsp stream?

Regards,
Matt

---

