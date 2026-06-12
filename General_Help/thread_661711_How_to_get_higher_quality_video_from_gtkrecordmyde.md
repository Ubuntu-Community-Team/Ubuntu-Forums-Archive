---
title: "How to get higher quality video from gtkrecordmydestkop"
date: 2008-01-08
forum: General Help
---

### Post by billgoldberg on 2008-01-08
I'm making some how-to video and I use gtkrecordmydesktop to do them.

However the quality isn't high enough. I want crystal sharp quality.

Is this possible with ogg theora?

I need to convert the videos to .avi using winff but they don't loose any quality, it's just gtkrecordmyedesktop that isn't producing the desired quality.

How can I fix that?

a video example:
[http://www.veoh.com/videos/v2392861X34bJdfJ](http://www.veoh.com/videos/v2392861X34bJdfJ)

---

### Post by eye208 on 2008-01-08
> **billgoldberg said:**
> How can I fix that?

a video example:
[http://www.veoh.com/videos/v2392861X34bJdfJ](http://www.veoh.com/videos/v2392861X34bJdfJ)
You can fix that by using a video hosting service that does not squeeze high resolution screen captures into 540x432 Flash video clips.

This is not recordmydesktop's fault at all. I'm sure the file you uploaded was much better quality.

Try [http://blip.tv/](http://blip.tv/).

---

### Post by billgoldberg on 2008-01-08
Yeah, I know veoh isn't the best. But still I would want to know how to improve gtkmydestkop quality.

The original really isn't much better than the veoh one.

---

### Post by eye208 on 2008-01-08
I've used recordmydesktop for quite a while now. If you record at 100% quality, the result will be excellent, but of course the file will be very large too since Theora is not the best codec in terms of compression ratio. The solution is _not_ to record at lower quality, but to transcode the high quality Theora stream to H.264 afterwards.

Blip.tv will host the video file in exactly the format that you upload. They will make a Flash version of it too, but you can select the original file to be shown by default. They will also host video in Ogg format, but I suggest you upload MP4 instead. You can transcode the Ogg Theora file to Quicktime-compatible H.264 using MEncoder and MP4Box for muxing. I recommend MP3 for audio because LAME will give you better quality than FAAC, the free AAC codec.

Transcoding/muxing can be done like this:

mencoder input.ogg -vf harddup -ovc x264 -x264encopts no8x8dct:crf=27 -nosound -mc 0 -noskip -of rawvideo -o output.h264

mencoder input.ogg -ovc raw -oac mp3lame -lameopts vbr=4:aq=0:q=6:lowpassfreq=-1:highpassfreq=-1 -mc 0 -noskip -of rawaudio -o output.mp3

MP4Box output.mp4 -new -fps *<insert fps here!>* -add output.mp3 -add output.h264

In the first MEncoder call, lower values of crf will increase video quality. In the second call, lower values of q will increase audio quality. Change these values until you are satisfied with the results but keep an eye on the resulting bit rate as well if you want the video to be streamable.

---

