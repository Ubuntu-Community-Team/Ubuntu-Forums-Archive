---
title: "microphone not working"
date: 2007-12-09
forum: General Help
---

### Post by ljalg on 2007-12-09
I've seen tons of postings but still can not get my mic to work in an application (sound recorder and others).  
[LIST]
[*]Speakers are fine
[*]I've enabled all items in volume control and turned all volumes up
[*]Sound card driver HDA ATI SB (Alsa mixer)
[*]I can hear my own voice from mic to speakers using analog mix as volume (can't be 100%, too much feedback)
[*]All capture devices are set to mic
[/LIST]

output of amixer is

```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Front Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 39
  Mono:
  Front Left: Playback 39 [100%] [0.00dB] [on]
  Front Right: Playback 39 [100%] [0.00dB] [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'PCM' 'ADC1' 'ADC2' 'ADC3'
  Item0: 'PCM'
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 54 [100%] [22.50dB] [on]
  Front Right: Capture 54 [100%] [22.50dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 54 [100%] [22.50dB] [on]
  Front Right: Capture 54 [100%] [22.50dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 54
  Front Left: Capture 54 [100%] [22.50dB] [on]
  Front Right: Capture 54 [100%] [22.50dB] [on]
Simple mixer control 'Analog Mix',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 19 [61%] [-18.00dB] [on]
  Front Right: Playback 19 [61%] [-18.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD' 'Aux' 'Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD' 'Aux' 'Mix'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD' 'Aux' 'Mix'
  Item0: 'Mic'
```

Any help is appreciated.

thank you

ljalg  :(

---

### Post by fwilliams on 2007-12-09
I had the same issue.

Had to go into the following:
gnome-volume-control

In the options tab I had to change Front Mic to Mic for all the inputs.

---

### Post by NilsE on 2007-12-09
> **fwilliams said:**
> I had the same issue.

Had to go into the following:
gnome-volume-control

In the options tab I had to change Front Mic to Mic for all the inputs.

He is correct.  You may also want to change to Front Mic and see what it does.

---

### Post by ljalg on 2007-12-09
Thank you both for the replies.  I've tried both ways with no luck, all input sources as mic and all input sources as front mic.  

My mic is plugged into the audio input plug (stereo din) on the back of the computer so I figured it should be mic, but you never know.

Any other ideas are appreciated.

ljalg

---

### Post by Dave Otter on 2007-12-09
Try going to volume control-edit-enable mic,mic capture and mic boost +20db.
   tho I expect you have done so already

---

### Post by philinux on 2007-12-09
This is a serious bug for gutsy

---

### Post by miershpedankl on 2007-12-14
I am not having the same problems, but I'll use this thread since it already exists. :)  I am not able to get ANY mic action going.  I can listen to music, so the sound works obviously.  Who knows what I have done to mess things up.  I attempted to get my BT headset to work with Skype, to no avail, so I could have changed some defaults or something.  Can anyone advise where to start over?  Can you give me some advice to go from if I get everything reset??

Thanks,
miershpedankl

---

### Post by Billsey on 2007-12-16
I have to agree with Philinux here. This is a serious bug.

Also, I have noticed another oddity (possibly in connection to the dead mic bug), whenever I run "Applications/Add-Remove" I find that ArdourGTK2 is ghosted and cannot be selected for download.

My mics are also dead (both machines: 1 GHz Celeron and 531MHz Pentium3; both running Gutsy; both with 384 MB RAM; Celeron has 160 GB HD; P3 has two HDs totalling 90 GB). This happened with the upgrade to Gutsy. Sound output is fine on both machines. The Celeron has built-in sound capability; the P3 has a Sound Blaster Audigy SE. Sound output works great on both.

I use the sound recording to do my devotional recordings that I call [Chats]("http://billsey-christian.net/mp3s/Chats"), so I would love to have this fixed. I **can** still do them on my Mac with the boom mic, so all is not lost, but it's a lot nicer to do it in the living room with the headset mic that allows me to move around as I record (in case anyone asks, very long patch cords :)).

---

### Post by Billsey on 2007-12-16
OK, so that didn't work either. :)

---

### Post by jespdj on 2007-12-16
What hardware do you have?
Did you search the [Launchpad bug database]("https://launchpad.net/ubuntu")?

The internal microphone in my XPS M1330 doesn't work by default, but there's a fix available (see [bug # 147682]("https://bugs.launchpad.net/dell/+bug/147682")).

---

### Post by Billsey on 2007-12-17
As posted in my first message in this thread:

> My mics are also dead (both machines: 1 GHz Celeron and 531MHz Pentium3; both running Gutsy; both with 384 MB RAM; Celeron has 160 GB HD; P3 has two HDs totalling 90 GB). This happened with the upgrade to Gutsy. Sound output is fine on both machines. The Celeron has built-in sound capability; the P3 has a Sound Blaster Audigy SE. Sound output works great on both.

Both mics just plug into the microphone input on the back of each machine.

Someone said something about "esound" correcting their problem. Perhaps I'll try that.

---

### Post by danwood76 on 2007-12-17
You could try compiling the latest ALSA driver and libs, this solved audio problems on my laptop.

Its not a bug with gutsy but with the alsa audio drivers, There are many different configurations for each piece of hardware and alsa tries to guess the best one for your hardware IDs. Its often helpful to try a few configurations.

---

