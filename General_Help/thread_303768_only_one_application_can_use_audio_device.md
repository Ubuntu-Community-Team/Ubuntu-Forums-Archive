---
title: "only one application can use audio device"
date: 2006-11-20
forum: General Help
---

### Post by xenoalien on 2006-11-20
My audio device can only be used with one application at a time. Is there a way to change this? (more than one application useing the audio device)

---

### Post by deanlinkous on 2006-11-20
what audio device do you have? Likely the device is your problem. Are you using Ubuntu?

---

### Post by NT4usB on 2006-11-20
I'll piggy back on this thread because I have a similar question. When I run Mythtv (presumably, it's using mplayer or some such for it's video) and another instance of mplayer, I get an error that some other device is using the audio (duh, I know... Mythtv) so I get no audio from the mplayer.
I'm using onboard sound and alsa but it acts the same with oss.
It's really not a big deal as the only time I run both is when I'm looking for a mythtv file to burn or sorting videos, etc.
I don't *usually* watch two videos at once..*g*

---

### Post by xenoalien on 2006-11-20
I have a Nvidia ck804. And I am using Ubuntu 6.10.

---

### Post by deanlinkous on 2006-11-20
no real suggestion....
could probably tweak settings, insert modules, mess around and get it to work or might look into polypaudio aka pulseaudio

---

### Post by xenoalien on 2006-11-20
How would I install pulseaudio on Ubuntu?

---

### Post by aysiu on 2006-11-20
Maybe try this?

Go to System > Preferences > Sounds and uncheck the box that says "Enable software sound mixing."

---

### Post by deanlinkous on 2006-11-20
good info aysiu!
So will their hardware mix sounds?

---

### Post by superm1 on 2006-11-21
> **NT4usB said:**
> I'll piggy back on this thread because I have a similar question. When I run Mythtv (presumably, it's using mplayer or some such for it's video) and another instance of mplayer, I get an error that some other device is using the audio (duh, I know... Mythtv) so I get no audio from the mplayer.
I'm using onboard sound and alsa but it acts the same with oss.
It's really not a big deal as the only time I run both is when I'm looking for a mythtv file to burn or sorting videos, etc.
I don't *usually* watch two videos at once..*g*

What you will want to do is change the audio device for mythtv from /dev/dsp and /dev/mixer to be ALSA:default

Just like that for both boxes:

```
ALSA:default
```

---

### Post by steevk on 2006-11-21
I have this problem as well. I use Kubuntu, though...if I'm using Amarok, YouTube won't play sound, and if I have YouTube up, WoW won't play sound...

---

### Post by NT4usB on 2006-11-21
> **superm1 said:**
> What you will want to do is change the audio device for mythtv from /dev/dsp and /dev/mixer to be ALSA:default

Just like that for both boxes:

```
ALSA:default
```

I've been playing with these settings for months. (I think I want to) get the remote control to adjust PCM instead of Master or Front. Maybe I'm wrong on this.
Right now, If I have the TV volume up high enough that I can get reasonable volume at 30% on MythTV, The volume won't go low. 2% is still very audible and the next increment is zero.
If I start with the TV set lower, I'm at 70% before I can get decent sound.
I did stumble upon ALSA:default in my googlings but only replacing /dev/dsp. Tried it and it didn't make a difference.
I'll use it both places and see what happens.
Every since I upgraded to 0.20 I haven't got all the remote settings back to where I like them. No longer can control mplayer volume, remote button response sux, etc. 
btw, MythTV will step frame by frame via > or < on the remote when paused. Do you know of a way to make mplayer step a frame at a time using the remote? I can get one second steps but not frame by frame.

---

### Post by NT4usB on 2006-11-21
Thanks superm1!
ALSA:default worked. Volume works good and I can launch two video apps without that annoying error.

---

