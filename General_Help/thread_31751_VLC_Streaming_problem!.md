---
title: "VLC Streaming problem!"
date: 2005-05-04
forum: General Help
---

### Post by nemesa on 2005-05-04
Please help me it's really important!!

I have some problem with vlc. (I've got it with apt-get). Sooo.... I can transcode to some format, but I've problem with audio mp3 encoding:

mux_ps private: Open
[00000289] mpeg_audio packetizer: MPGA channels:2 samplerate:48000 bitrate:128
[00000304] ffmpeg encoder error: cannot find encoder MPEG Audio layer 1/2/3
[00000240] stream_out_transcode private error: cannot find encoder
[00000240] stream_out_transcode private error: cannot create audio chain

how can i load mp3 encoders? maybe lame?? If I install ffmpeg it doesn't help...

Please Help!

---

### Post by nemesa on 2005-05-05
It's really important please help!

---

### Post by kvidell on 2005-05-05
[QUOTE=nemesa]It's really important please help![/QUOTE]
 This is a shot in the dark, because I have no idea if it would help or not, I'm assuming it couldn't hurt by any means... but:
Do you have the w32codecs package installed?
- Kev

---

### Post by nemesa on 2005-05-07
I have some w32codecs for mplayer.... but.. i can't understand why is it so important...

---

