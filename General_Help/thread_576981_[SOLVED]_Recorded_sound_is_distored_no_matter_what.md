---
title: "[SOLVED] Recorded sound is distored no matter what recoriding software I use."
date: 2007-10-15
forum: General Help
---

### Post by applegrew on 2007-10-15
I have on board Realtek sound chipset. In fact I am a bit confused. It shows like I have 3 cards Intel ICH5 (Alsa Mixer) Realtek ALC 655 rev 0 (OSS Mixer) and SAA7134 (Alsa Mixer) (Well this for my TV Tuner card not the sound card).

Whatever I try to record from /dev/dsp (for Line-In selection or Mic, etc.) gives me distorted sound. I have attached a tar.gz file with the mp3 of the recording. The original sound had no such noise. I have played with the Volume levels a lot and none helped at all.

Please help.](*,)

---

### Post by applegrew on 2007-10-16
pls help. say something...............................

---

### Post by applegrew on 2007-10-16
Any ides?????

---

### Post by Samhain13 on 2007-10-16
I can offer no solution. But I'm posting just to say that I have the same issue.
There's always lots of distortion when recording from the mic. Lowering the input level just makes everything (distortion and speech) softer.

---

### Post by applegrew on 2007-10-16
Thanks for the reply. I have already tried all volume adjustment things, but I just now tried arecord and it **records well.** :D I used the following command.
```
arecord -f cd -t wav t.wav
```
Apparently it is using Alsa device and not the OSS device (as was in the previous case). The probelm now is how do I tell mencoder and transcoder to use this alsa device and I am not sure which device this is. Below is the output of **arecord -l**
```
**** List of CAPTURE Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 1: Intel ICH - MIC ADC [Intel ICH5 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 2: Intel ICH - MIC2 ADC [Intel ICH5 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 3: Intel ICH - ADC2 [Intel ICH5 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SAA7134 [SAA7134], device 0: SAA7134 PCM [SAA7134 PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and below is the output of **cat /proc/asound/pcm**
```
00-04: Intel ICH - IEC958 : Intel ICH5 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel ICH5 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH5 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH5 - MIC ADC : capture 1
00-00: Intel ICH : Intel ICH5 : playback 1 : capture 1
01-00: SAA7134 PCM : SAA7134 PCM : capture 1

```

Any suggestions?

---

### Post by Samhain13 on 2007-10-16
Sorry, what you have above is already beyond my understanding. :)
But I'll give arecord a try.

---

### Post by applegrew on 2007-10-16
It seems the OSS driver for my card has the issue not the alsa driver hence during playback I hear no distortion (alsa is used here), but during recording (where OSS was being used) I hear so much distortion.

---

### Post by applegrew on 2007-10-16
Yeeeeeeeeeeeeeeeeeeeeeeeeeeessssssssssss I did it.\\:D/:-\"

Now the sound recording too is perfect! I have used the following command.
```
mencoder \
-o out.avi \
-ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000:vhq \
-oac mp3lame -lameopts preset=standard:mode=1 \
-vf crop=688:560:14:0,expand=704:576,dsize=4/3 \
-af volume=-5 \
-ofps 25 -srate 48000 \
-tv driver=v4l2:norm=PAL:outfmt=yv12:input=0:width=704:height=576:amode=1:alsa:adevice=default \
tv://
```

---

### Post by Samhain13 on 2007-10-16
Hey! Congratulations!

I'll be bookmarking this thread and I'll try the solution you have in the very near future. Will post feedback once I've tried it. :D

---

### Post by applegrew on 2007-10-16
@Samhain13  hey thanks man. :D

Just droped by to say that how did I hit upon the 'default' hardware id, after all there is a whole lot of confusion over what actually is this hardware id which mencoder/mplayer expects. Just run the command
```
arecord -L
```
Note it is capital L not samll l.

This shows a sort of sudo code of some PCM devices (like **hw**) and some various other PCM devices including '**default**'. From the sudo code of **hw** it seems that we need to pass the hardware id as : **hw=<card no>.<device no>.<subdevice no>** All of these codes can be found out using **arecord -l** . Well I haven't tried this so, I don't guarantee that this syntax is the correct one.

---

### Post by applegrew on 2007-10-16
I am loving it. Here is how to make transcode work. Simple just use the alsa oss wrapper called **aoss** (from the **alsa-oss** package). Complete sheel script below.
```

#!/bin/sh

# The original code is from the url below.
# http://www.transcoding.org/cgi-bin/transcode?Video4linux_Examples
# make sure to eg sudo modprobe saa7134-oss -v to get audio
# set channel with mplayer, quit, start recording, start mplayer for further change of channel during recording

TODAY=$( date +%Y%m%d )
NOW=$( date +%H:%M )
aoss transcode \
        -x v4l2=resync_margin=1:resync_interval=250,v4l2 \
	-g 640x480 \
	-p /dev/dsp \
        -i /dev/video0 \
	-e 32000,16,2 \
	-Q 3 \
        -N 0x55 \
        -J pp=hb/vb/al/tn/ci,resample,smartyuv,pv \
        -w 4000 \
        -y ffmpeg \
        -F mpeg4 \
        -o ${TODAY}-${NOW}-recording.avi \
        --avi_limit 1536 \
	--lame_preset standard \
	--encode_fields t

```

The advantage of using transcode over mencoder is that it has many cool plugins like we can view and record the plugin. We can also put our own logo.

---

### Post by Samhain13 on 2007-10-16
My recordings are still noisy. But I'm thinking that perhaps my headset is grounded.
Thanks for topic, at least I learned a bit about arecord and aplay. :D

Cheers!

---

### Post by applegrew on 2007-10-16
no probs. :) BTW do you knwo about any good program that can capture from my tv tuner and stream that over network? For some reason don't why vlc is not able to capture.

---

### Post by applegrew on 2007-10-26
> **applegrew said:**
> I have on board Realtek sound chipset. In fact I am a bit confused. It shows like I have 3 cards Intel ICH5 (Alsa Mixer) Realtek ALC 655 rev 0 (OSS Mixer) and SAA7134 (Alsa Mixer) (Well this for my TV Tuner card not the sound card).

Whatever I try to record from /dev/dsp (for Line-In selection or Mic, etc.) gives me distorted sound. I have attached a tar.gz file with the mp3 of the recording. The original sound had no such noise. I have played with the Volume levels a lot and none helped at all.

Please help.](*,)
I just came by to add that I think I have figured out why the sound hears like that (as it hears in the sample I provided). I have found that when the capturing sample rate is below the actual sample rate of the card then it hears like that. The amount of distortion depends on the difference between the two sampling rates. In the sample sound I attached the actual bitrate was probably 48000 but the capturing was being done at only 8000. Probably the sampling rate for my /dev/dsp was configured so.

---

