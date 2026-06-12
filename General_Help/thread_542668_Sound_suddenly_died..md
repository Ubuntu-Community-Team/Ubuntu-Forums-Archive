---
title: "Sound suddenly died."
date: 2007-09-04
forum: General Help
---

### Post by the_it on 2007-09-04
I installed Feisty for me  and my brother a few months ago and everything's been working pretty fine for a while now.  This morning I get up and go to work and when I go home my brother tells me sound is dead.

I confirm it.  I cannot play sound.  Everything acts like sound exists: no players complain, no error messages or anything.  But sound does not go out.

I go through a few checks
First sound is loaded.
```
markd@trixie:~$ lsmod|grep snd
snd_rtctimer            4576  1 
snd_hda_intel          23584  0 
snd_hda_codec         256384  1 snd_hda_intel
snd_pcm_oss            47616  0 
snd_pcm                89480  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          18816  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi           10240  0 
snd_rawmidi            28672  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                58272  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26120  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9492  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66472  11 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
snd_page_alloc         11024  2 snd_hda_intel,snd_pcm
```

Next, volume is not 0.  I used alsamixer to check, and everything is at max.  Nothing is muted either.

Next, nothing's using my sound.  IIRC anyways, I should get a complaint if something is using sound.

```
markd@trixie:~$ lsof |grep snd
 markd@trixie:~$ lsof |grep dev|grep audio
markd@trixie:~$ 
```

I then tried playing something on the command-line using mplayer to make sure it wasn't esd.  No joy at all.
```
markd@trixie:~$ mplayer /home/sounds/Hybrid\ -\ If\ I\ Survive.mp3 
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sounds/Hybrid - If I Survive.mp3.
Audio file file format detected.
Clip info:
 Title: If I Survive
 Artist: Hybrid
 Album: Wider Angle Special Edition - 
 Year: 
 Comment: 
 Track: 2
 Genre: Unknown
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  13.1 (13.1) of 521.0 (08:41.0)  1.9% 
```
mplayer seems to be acting as if nothing was the matter, but the silence is killing me.

Just to make sure that it wasn't hardware, I rebooted to the other OS.  I get the windows login and shutdown properly so it's a linux specific thing.  But I don't know what.

What pointers can you give that I could check?

```
markd@trixie:~$ uname -a
Linux trixie 2.6.20-16-lowlatency #1 SMP PREEMPT Wed Aug 15 15:42:48 PHT 2007 x86_64 GNU/Linux
```
Running on Feisty 64bit.

This is an Asus P5L-MX mobo with the Intel ICH7 onboard sound.

I asked my brother if the system asked for updates that he agreed to (I was guessing something borked my sound configuration) but he didnt see nothing.

---

### Post by the_it on 2007-09-04
bump

---

### Post by the_it on 2007-09-04
And just as suddenly as it arrived, it disappeared. hmmm oh well.

---

### Post by rax_m on 2007-09-04
Did you have to do anything special to get sound working in the first place?
Like install the lates alsa drivers?

I had to do that and everytime a linux-header / kernel update comes thru I have to re-apply the alsa drivers...

---

