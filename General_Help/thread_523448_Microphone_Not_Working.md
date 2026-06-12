---
title: "Microphone Not Working"
date: 2007-08-11
forum: General Help
---

### Post by arbulus on 2007-08-11
I've searched around the forums and I've Googled like crazy, but I've not been able to find a solution to this.

I'll start with my box's specs:
Dell dimension E521, AMD Athalon 64bit Dual Core Processor @ 1.9Ghz, 1GB RAM, Ubuntu Feisty, integrated nVidia Graphics and integrated sound.

I've recently purchased a Plantronics Audio 300 microphone.  I cannot get this microphone to work.  Neither Audacity or Sound Recorder will recognize any input from it.  I've have tried the tips [here]("http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/") and [here]("http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html") but with no success.  The second link there mentions finding the "capture" setting in the preferences of the audio settings, but that doesn't exist in my audio settings.  But I have checked all of the other options and made sure that nothing was muted.  i have also run alsamixer and made sure that everything is unmuted and that all of the volumes are turned up.  But still my microphone will not work.

I'm really at a loss here now.  Nothing in the forums here has helped at all and nothing I've found googling has helped at all.  I know that people do in fact have mics that work under Ubuntu, so it's obviously not impossible.  So I'm just not sure where I'm going wrong here.

Any help is greatly appreciated.

Thanks!

---

### Post by kutta on 2007-08-12
for me too audacity and sound recorder didnt work..but try skype test call service to check ur uphone.....

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)   try ur luck here....

for me [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19)  worked for skype but not for audacity and sound recorder... gud luk

---

### Post by arbulus on 2007-08-12
> **kutta said:**
> for me too audacity and sound recorder didnt work..but try skype test call service to check ur uphone.....

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)   try ur luck here....

for me [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570/comments/19)  worked for skype but not for audacity and sound recorder... gud luk


Still no luck.

Skype will hear a very fuzzy, distorted, almost inaudible recording but Audacity and Sound Recorder still don't recognize the mic at all.

---

### Post by ugm6hr on 2007-08-12
Post the output from:
```
amixer
```

This is how I got mine to work:
[http://ubuntuforums.org/showthread.php?t=506515](http://ubuntuforums.org/showthread.php?t=506515)

---

### Post by arbulus on 2007-08-12
Here you go.  The output of "amixer"

```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Front Left: Playback 89 [70%] [on]
  Front Right: Playback 89 [70%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Front Left: Playback 127 [100%] [on]
  Front Right: Playback 127 [100%] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Front Left: Playback 127 [100%] [on]
  Front Right: Playback 127 [100%] [on]
Simple mixer control 'ADCMux',0
  Capabilities: cswitch
  Capture channels: Front Left - Front Right
  Front Left: Capture [on]
  Front Right: Capture [on]
Simple mixer control 'InMux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%]
  Front Right: Capture 4 [100%]
Simple mixer control 'InVol',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%]
  Front Right: Capture 14 [100%]
Simple mixer control 'Input Source',0
  Capabilities:
  Mono:
```

---

### Post by ugm6hr on 2007-08-13
> Simple mixer control 'Input Source',0
  Capabilities:
  Mono:

I had to select an Input Source - but if that is all it says - there are no options to select.  Hmmm...

Afraid I can't help.

---

### Post by arbulus on 2007-08-18
Bump

---

### Post by arbulus on 2007-08-18
Ok, I tried plugging my microphone into my Macbook Pro and my iMac as well to see if those machines would recognize it fine.  They didn't.  No sound recognized from either one.  So, I assumed that the mic is defective, returned it to the store and got a different mic.

This new mic still does not work on any of my machines.

This is beyond frustrating.  A microphone should NEVER have to be configured; just like headphones - the machine should just know what to do with it.  No one should EVER have this kind of problem.  I cannot possibly comprehend what on earth could be the problem here.  I have done everything I've been able to find to make this thing work and still no luck. 

So here I am, still at a complete loss.  I do appreciate very much all of your suggestions so far, so please don't think I'm taking my frustration out on you all.  I'm not, I'm just venting.

---

### Post by ugm6hr on 2007-08-18
I know you have already unmuted everything in alsamixer, but just in case you haven't noticed that the Tab key swaps between playback / capture options - that is worth a try:
```
alsamixer
```

---

### Post by arbulus on 2007-08-19
I checked the alsamixer, and all of the input volumes are unmuted and at 100%.
However, I did try something different: under "input source" I have three options, "mic", "front mic" and "line".  I had it on "line", but I changed it to "mic" to see what would happen.  Sound Recorder and Audacity still don't recognize it, but when I do a Skype test call, I can hear a very distorted and fuzzy playback of myself, but nothing that could ever be useful.  It's almost totally inaudible.

---

### Post by ugm6hr on 2007-08-20
> **arbulus said:**
> I checked the alsamixer, and all of the input volumes are unmuted and at 100%.
However, I did try something different: under "input source" I have three options, "mic", "front mic" and "line".  I had it on "line", but I changed it to "mic" to see what would happen.  Sound Recorder and Audacity still don't recognize it, but when I do a Skype test call, I can hear a very distorted and fuzzy playback of myself, but nothing that could ever be useful.  It's almost totally inaudible.

Presumably you tried "front mic" too?  My laptop labels the external mic plug as front mic.

---

### Post by arbulus on 2007-08-20
> **ugm6hr said:**
> Presumably you tried "front mic" too?  My laptop labels the external mic plug as front mic.

Yeah, I tried that one too, with no luck.

---

### Post by arbulus on 2007-08-21
ok, so I started over.
I took my mic back to the store and picked up a USB mic.  All I had to do was unmute the input and it's working great so far.  I'm glad that it turned out much easier with this one.

Thanks for all your help.  I really appreciate it.

---

### Post by ugm6hr on 2007-08-22
No worries.

Shame I couldn't actually help!

---

