---
title: "How to control audio output from 2 apps or 2 browser instances"
date: 2022-03-18
forum: General Help
---

### Post by herculpirate on 2022-03-18
I have 2 apps
Squeezelite and Spotify.

How do I control audio output such that audio from only 1 app goes through to output.
Now i have to pause audio from one app and then move to another app and play.

I would like to start the audio on one app and the other app goes into PAUSE mode or stops playback

---

### Post by herculpirate on 2022-03-18
Is there also a method for 2 browsers and audio coming from 2 browser instances ?

---

### Post by MAFoElffen on 2022-03-20
No. Not Logically... Apples and oranges there in some respects. 

Audio players, that play in the background, even if it loses 'focus'... meaning you leave the application running in the background while doing other things, while it continues to play... Assume that is what it is supposed to do. That is how it was written, to connect to and take complete control over (applying an exclusive lock on) the audio device.

Browsers, and players within brower tabs work differently. They stop playing when the tab is changed to another tab, so the only audio you will hear is the tab that is in focus.

For what you are asking, the application would have to stop assuming it is alone in the world and have to learn to share. (Application writers do not like to share resources, and believe you should use theirs exclusively.) Next, to retain control and be able to do that, it would need another intermediate application to act as a device multiplexer. Where the 'player' application would send it to that application, as if was the audio device, and that application would decide how input and output was "traffic controlled".

I hope that description opens up an understanding to that. I am sorry that I do not know of anything like that.

---

### Post by Holger_Gehrke on 2022-03-21
> **MAFoElffen said:**
> For what you are asking, the application would have to stop assuming it is alone in the world and have to learn to share. (Application writers do not like to share resources, and believe you should use theirs exclusively.) Next, to retain control and be able to do that, it would need another intermediate application to act as a device multiplexer. Where the 'player' application would send it to that application, as if was the audio device, and that application would decide how input and output was "traffic controlled".

That kind of intermediary application actually exists. It's called a 'sound server'. That's what Pulse Audio is, which is installed on Ubuntu by default. All applications can continually send sound streams to the sound server and it will mix them in real time. With pavucontrol you can set the volume of each incoming stream or even mute a stream.

To control media playback from a different application than the player itself there is [MPRIS]("https://specifications.freedesktop.org/mpris-spec/2.2/") - the **M**edia **P**layer **R**emote **I**nterfacing **S**pecification - which a lot of players implement.  If Squeezelite and Spotify support MPRIS it should be possible to hack something together to control them. On XUbuntu I have a PulseAudio module for the panel which allows minimal control (previous,play/pause,next) for several MPRIS compatible players the module knows about.

Holger

---

