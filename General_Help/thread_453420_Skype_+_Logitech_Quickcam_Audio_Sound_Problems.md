---
title: "Skype + Logitech Quickcam Audio Sound Problems"
date: 2007-05-24
forum: General Help
---

### Post by GuerrillaWon on 2007-05-24
I'm sure anyone who uses Skype under Linux knows how terrible it is. They seemed to have just put out a shotty version for Linux and called it a day.

This leads to plenty problems, including mine, one which a lot of people also seem to have. Since I can't find any real decent information on fixing this problem, so I'm turning to you all for some personal help, I'd like to make an attempt with your help to get it up and running, and documenting how I did so fairly decently for others to use. I am ok with Linux as a user, not the best, not totally terrible. Along the lines of the average user I'd say.

On to the problem...

Here's what I am working with...

[B]Linux LinuxBox 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

Skype 1.3.0.53 for Linux

Logitech Quickcam Communicate STX (Bus 002 Device 005: ID 046d:08d7 Logitech, Inc.)[/B]

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

What I think as of now is that Skype uses OSS, or ALSA with an OSS compatibility layer. I believe the problem is that Skype under Linux is configured to both play back audio, and receive audio input from the same hardware. There is of course a conflict in that I am getting my audio output from my built in sound card (nvidia), and inputing audio through the webcams usb microphone.

This is where my problem comes in. Since I have a USB webcam with built in microphone, I am running into problems getting both to work from the same device.

It was working at one time, both audio and video, and now it does not. The problems with audio I have been running into are that, I believe if I have a flash video running from say youtube, and then I run movie player at the same time, movie player if the conditions are right, screw up my audio thus killing the sound I receive from flash videos along with a few other small problems, in which I have to reinstall flash to fix, or that it kills my mic and gives me "problem with sound device" errors in Skype and I can no longer use the microphone.

I am able to hear the person talking, but they cannot hear me. That is as far as I can get.

Sometimes I don't get past the "problem with sound device" error, and other times when I play with the sound settings in Skype from ALSA and OSS along with the audio inputs and outputs, I can at least be able to hear them and no sound errors are reported even though my webcam mic has no functionality.

The solution to this problem seems to be a program called **DSP Hijacker**. What I think this does, is it tricks Skype into thinking it is outputting and inputting audio from the same hardware.

I however cannot get this to work. I was wondering if anyone has any suggestions or thoughts on this problem. Any settings suggestions to try, or basically anything at all for me to play around with to see if I can't get this working.

Also what would be very helpful to me is if someone could tell me how to check my audio settings, or moreso what settings change when my flash video/audio, and my movie player video/audio run into spontaneous conflicts, both seriously maiming each other in the digital battlefield.

Any and all advice is greatly appreciated. Let me know if there's any other information that would be helpful to you.

---

### Post by GuerrillaWon on 2007-05-24
Anyone have any suggestions at all out there?

---

### Post by GuerrillaWon on 2007-05-24
Got it to work.

All I had to do was...

First see if I was running artsd by doing...

ps aux | grep artsd

I was, then I ran...

artsdsp -m et

I honestly am not sure exactly why this worked for me, but it did.

---

### Post by -G- on 2007-05-25
Just curious but have you had a go @ the new 1.4 Alpha second release --> [https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype) The devs are boasting equal audio quality to win3.2. Still no vid but is does feel closer than ever before.

-G-

---

### Post by GuerrillaWon on 2007-05-28
Sound went out again. Back to square one.

This... is... aggravating.

I have not tried the new version. I looked at it and wasn't sure if I should upgrade to it, and if so how. :/

---

### Post by GuerrillaWon on 2007-06-08
Now I've lost all sound.

I sure it's because I was running mplayer and a flash video at the same time.

UAResolved where are you? heeeeeelp!

*shines UAR symbol into the sky*

---

### Post by GuerrillaWon on 2007-06-08
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

Ahh yes here's my audio hardware.

---

### Post by fakie_flip on 2007-06-10
> **GuerrillaWon said:**
> 00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)

Ahh yes here's my audio hardware.

I also have that hardware.
```

chris@ubuntu:~$ lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
chris@ubuntu:~$ 
```

Here is what I've tried to get the game Legends working while running Skype. I modified the legends script to include artsdsp.

```
chris@ubuntu:/usr/games/legends$ artsd -s 1 &      
[1] 7732
chris@ubuntu:/usr/games/legends$ artsdsp -m ./runlegends
artsdsp works only for binaries
chris@ubuntu:/usr/games/legends$ sudo vim runlegends
Password:
chris@ubuntu:/usr/games/legends$ ./runlegends
chris@ubuntu:/usr/games/legends$ ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
grab_native: (path /dev/dsp fd 14)
set_fd in: bufsiz 4096 fmt 0x10 speed 44100 channels 2
set_fd out: bufsiz 1024 fmt 0x10 speed 44100 channels 2

chris@ubuntu:/usr/games/legends$ ./runlegends
chris@ubuntu:/usr/games/legends$ ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
open /dev/[sound/]dsp: Device or resource busy

chris@ubuntu:/usr/games/legends$ cat runlegends
#!/bin/sh
if [ -L $0 ]; then
        LEGENDS_DIR="$(dirname $(readlink $0))"
else
        LEGENDS_DIR="$(dirname $0)"
fi
cd $LEGENDS_DIR
export LD_LIBRARY_PATH=./
artsdsp -m ./LinLegends $* &
chris@ubuntu:/usr/games/legends$ 
```

---

