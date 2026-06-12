---
title: "encode video to put on cell phone??"
date: 2007-07-27
forum: General Help
---

### Post by Digitallysick on 2007-07-27
Im trying to put some videos on my cell phone, but to do so, i have to convert them with parameters such as these

maximum 350 kbps video bitrate
maximum 96 kbps audio bitrate
maximum 15 fps for non choppy video
maximum 320x240 for the size of the video

any program i can use to set these parameters? i would like to convert flvs to to mp4

---

### Post by kostkon on 2007-07-27
Just install ffmpeg. I recommend you to install the version of ffmpeg that is offered from the [medibuntu repository]("http://medibuntu.org/"). Thus, [add]("http://medibuntu.org/repository.php") this repository to your software sources and then install the software from Synaptic.

A good GUI for ffmpeg is [WinFF]("http://biggmatt.com/winff/").

There is already a preset in WinFF for video for mobile phones, maybe it will work for you right away, otherwise you can adjust it to your needs.

There are other GUIs for use with ffmpeg. If you don't like WinFF just search for another one. But, ffmpeg is the absolute solution for your conversion needs. You will be able for sure to convert an flv video to MPEG4.

I hope I helped you somehow :)

---

### Post by Tsen on 2007-07-27
Also, most phones only can play .3gp or .3g2 formats. 
You might already know this, but here's the important info on the formats:
> .3gp 3GPP standard, GSM Network, Video: MPEG-4, H.263, Audio: AAC, AMR
.3g2 3GPP2 standard, CDMA2000 Network, Video: MPEG-4, H.263, Audio: AAC, AMR, QCELP.

---

