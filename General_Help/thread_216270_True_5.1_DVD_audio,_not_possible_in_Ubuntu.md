---
title: "True 5.1 DVD audio, not possible in Ubuntu?"
date: 2006-07-15
forum: General Help
---

### Post by Denis on 2006-07-15
Hi

I'm having a problem with 5.1 sound when playing a DVD. The audio plays through the 6 speakers, but it plays stereo sound instead of 5.1. 

This can easily be heard because the voice plays on the rear and front speakers, while it should only play on the center speaker. Also the surround effects are missing, the front sound is the same as the rear. It seems like the 5.1 sound is downmixed to stereo and spread to the 6 speakers. 

This happens with all these players: VLC, Totem, Gxine and Mplayer. I use ALSA for the sound. 

5.1 playback works well on Windows and also on the [Kororaa XGL liveCD]("http://kororaa.org/static.php?page=static060318-181203"). Gxine, Totem and Kaffeine played true 5.1 sound in Kororaa (VLC didn't however). It seems like it's not a problem with Linux systems, so it must be possible to do it on a Ubuntu OS. 

I have a Creative Soundblaster Audigy 2 ZS, connected to a 5.1 speaker setup. I'm now running Ubuntu Dapper Drake and I had this flaw ever since Hoary Hedgehog.  

There must be other people who also experience this problem. Has anyone got a solution? I've read other threads about this topic, but none of them provided an answer.

---

### Post by jordilin on 2006-07-15
The eternal problem :( In my case I'm unable to watch commercial dvd movies. I've post the problem but no definitive answer. In your case, have you tried to set up the audio controls by means of alsamixer. Type alsamixer.

---

### Post by iggee85 on 2006-07-15
I use mplayer as my main media player. To enable 5.1 in mplayer go to:
/home/username/.mplayer
Open "config" and add "channels = 6", now try opening a dvd or any 5.1 movie and see if it works.

Also type "alsamixer" in console and check to see that none of the necessary channels are muted.

To enable in xine, I think you have to go to: /home/username/.xine
Then go to the xine config file and you have to set audio to "surround5.1" (use the search function for "surround5.1").

---

### Post by Denis on 2006-07-15
> **iggee85 said:**
> To enable 5.1 in mplayer go to:
/home/username/.mplayer
Open "config" and add "channels = 6", now try opening a dvd or any 5.1 movie and see if it works.That defenitely does something. The voice is now no longer played with the left and right speakers. But the center speaker doesn't play the voice either (just background sound). The result is that I hear no talking. 

> **iggee85 said:**
> Also type "alsamixer" in console and check to see that none of the necessary channels are muted.

To enable in xine, I think you have to go to: /home/username/.xine
Then go to the xine config file and you have to set audio to "surround5.1" (use the search function for "surround5.1").I've checked alsamixer before, everything looks right here. Front, Surround, Center and LFE are all unmuted.

The Xine config allready has: audio.output.speaker_arrangement:Surround 5.1, but no surround when playing.

---

### Post by iggee85 on 2006-07-16
Ok try this; enter "speaker-test -Dplug:surround51 -c6" in terminal.
You should hear white noise from all 6 channels. Check man speaker-test if you wanna play around with the settings.
Post your results.

---

### Post by WickedImp on 2006-07-16
Hi there. Having the same 5.1 problem. Also using ALSA on an Audigy2 NX (USB). I tried speaker-test and the following happens:
```

ssuhl@svenlinux:~$ speaker-test -Dplug:surround51 -c6

speaker-test 0.0.8

Das Wiedergabegerät ist plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:1972:(snd_pcm_open_conf) Invalid type for PCM surround51 definition (id: surround51, value: cards.pcm.surround51)
Playback open error: -22,Invalid argument
...

```

If I skip the -D option it will use 6 channels on whatever it uses to play it. Also I hear sound from different speakers, but if the output says it plays sound on '5 - Low Frequency Effects (Subwoofer)' it plays it somewhere else.

Anyway - how can I get information about what devices are supported by my PCM driver? Where can I do cat /proc/asound... to get all this devices listes (i.e: plug:surround40, plug:surround51, etc...)? Never figured this out.

---

### Post by Denis on 2006-07-16
"speaker-test -Dplug:surround51 -c6" didn't work, the output is: 
```

speaker-test 0.0.8

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:1107:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directoryALSA lib conf.c:3951:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM surround51
Playback open error: -2,No such file or directory

```
"speaker-test -Dplug:surround51:1,0 -c6" also doesn't work. 
Neither does "speaker-test -Dsurround51 -c6". 

"speaker-test -D**surround51:1,0** -c6" does work and outputs this: 
```

speaker-test 0.0.8

Playback device is surround51:1,0
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 16 to 16384
Periods = 4
Buffer time size 2525
To choose buffer_size = 16384
To choose period_size = 4096
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 17.585341
```

This works very well, the sound comes from the appropriate speaker.

---

### Post by iggee85 on 2006-07-16
@WickedImp:
Yeah, I believe the LFE plays on all speakers. On my system it comes from more than one speaker. You could try playing around with the sound rate to see how low your sub can play it.

@Denis
Here is my mplayer config:

# Write your default config options here!
xo = xv
monitoraspect = 4:3 #16:9
double = yes
ao = alsa
channels = 6
nolirc = yes
nojoystick = yes

First delete your .mplayer folder, then open mplayer. When the new folder is created paste this code into config. Now try opening a dvd with mplayer.

---

### Post by Denis on 2006-07-16
Using your mplayer config has the same effect as using mine. 5.1 sound is played, but the center channel plays something wrong. 
I have to change the device to hw=1.0 in order to hear any sound (because hw=0.0 is the internal soundcard)

I also tried "mplayer dvd:// -channels 6 -ao alsa:mmap:device=hw=1.0 -double yes" which gives the same result. 
In the console (part of) the output is: 
```

Building audio filter chain for 48000Hz/6ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: hw:1,0
alsa-init: mmap set
alsa: 48000 Hz/2 channels/4 bpf/32768 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/6ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...

```

---

### Post by iggee85 on 2006-07-16
Here's my output on playing a DVD:

```

Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.1 (3f+2r+lfe)  48000 Hz  448.0 kbit/s
AUDIO: 48000 Hz, 6 ch, s16le, 448.0 kbit/9.72% (ratio: 56000->576000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 48000Hz/6ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: surround51
alsa: 48000 Hz/6 channels/12 bpf/196608 bytes buffer/Signed 16 bit Little EndianAO: [alsa] 48000Hz 6ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/6ch/s16le -> 48000Hz/6ch/s16le...
Starting playback...

```

For some reason your alsa is downmixing to stereo. I would check the restricted formats wiki, because this is what i used to setup my media. (I only use mplayer with the latest w32codecs installed). The only solutions I can think of is that either you don't have the right codecs installed or your libdvdcss isn't setup properly. 

[HTML]https://help.ubuntu.com/community/RestrictedFormats[/HTML]

---

### Post by Denis on 2006-07-17
I've looked around on the forums and did some tests with my Kororaa XGL and Ubuntu Dapper Beta2 liveCD. Unfortunately I didn't make any progress. 

I don't think it has something to do with the codecs or libdvdcss. I've got w32codecs (version 1:20050412-0.0) and libdvdcss2 (version 1.2.8-1~5.04ubp1) installed. That w32codecs package was the latest one, I've looked that up recently. The libdvdcss package won't matter, because the same problem occurs when playing avi files with AC3 sound. 

I did see that the Kororaa XGL liveCD has a newer alsa version. 
cat /proc/asound/version shows: 
Advanced Linux Sound Architecture Driver Version 1.0.11rc4.
Compiled on Mar 25 2006 for kernel 2.6.16-archck1 (SMP).

In ubuntu it says: 
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 
(Mon Nov 07 13:30:21 2005 UTC).

Also the sliders in the volume contol program work differently in Kororaa: PCM Center, PCM Front, PCM LFE and PCM Surround have an effect on the playback, while Front, Surround, Center and LFE sliders have no effect. In Ubuntu this is just the opposite.Maybe this has something to do with the different version of alsa...

I also tried disabling the internal soundcard, but this has no effect (besides the number changing of devices). 

I've really tried all I could, but without any succes this time. Maybe I'll just have to wait for a newer verion of alsa or mplayer in future Ubuntu releases. I'll also report a bug about this at launchpad. 

Thanks for your help iggee85. I did learn more about what the problem is.

(bug report: [https://launchpad.net/distros/ubuntu/+bug/53516](https://launchpad.net/distros/ubuntu/+bug/53516) )

---

### Post by reclusivemonkey on 2006-07-17
I'm afraid I can't offer any help Denis, but I can point you to some samples to test things out if you do find a fix ;-)

[http://www.cinenow.com/us/vobtrailer.php3](http://www.cinenow.com/us/vobtrailer.php3)

---

