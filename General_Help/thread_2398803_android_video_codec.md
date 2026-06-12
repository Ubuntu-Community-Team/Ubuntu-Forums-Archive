---
title: "android video codec"
date: 2018-08-17
forum: General Help
---

### Post by hmiersch on 2018-08-17
hi.  i just tried putting a video on my S6. it transferred ok (although not as fast as i would have liked) but the problem was that when i tried to play it on the phone, it told me it could not play the video because of an "unsupported video codec.". the video is encoded in h264 in an mp4 container. is there something i can install on the phone to make this work? re-encoding all my videos with another encoder is not an option because i have too many of them.

---

### Post by TheFu on 2018-08-17
There are many, many, different levels of h.264 encoding. You need to find out which the S6 supports and only encode to that level.  You can script the re-re-re-encoding, if you want it to work.  ffmpeg can be scripted for that, but until you can know the S6 supported levels, not much point.

I recorded a show and used handbrake to transcode into h.264/mkv.```

| + Duration: 1529.000s (00:25:29.000)
|  + Codec ID: V_MPEG4/ISO/AVC
|  + CodecPrivate, length 47 (h.264 profile: Main @L4.0)
|  + Codec ID: A_AAC
|  + CodecPrivate, length 2
|   + Channels: 2
```

This is the output from mkvinfo.  The "Main @L4.0" is the h.264 level.

---

### Post by hmiersch on 2018-08-17
I installed vlc on my phone, hoping that would install the right codec. Now I can play the video in vlc, but video still gives me the same error. So whatever vlc uses to play that video, it is not available system-wide. That will probably be a problem for people who want to write their own media player.

---

### Post by TheFu on 2018-08-17
Good solution, if vlc works well on your device. It doesn't on many.

vlc is statically linked to ffmpeg libraries to avoid codec issues, assuming they aren't trying to include tracking files played in the codec implementations, which was done with some proprietary codecs on "other" platforms with centralized video codec management.

If you use vlc, you can look at the video codec properties to determine the details of the h.264 encoding.

---

### Post by SeijiSensei on 2018-08-18
I find that the MXPlayer Android app plays everything mpv on my computer can.

---

### Post by Yellow Pasque on 2018-08-19
Run mediainfo on one of the files that doesn't play (You can remove personal info like title if you wish):
```
sudo apt-get install mediainfo
mediainfo filename.mp4
```

---

