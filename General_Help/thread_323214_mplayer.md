---
title: "mplayer"
date: 2006-12-21
forum: General Help
---

### Post by jdm2 on 2006-12-21
I have my sound set up properly so I can have everything playing at one if I want to but mplayer is configured wrong.  Can you help me out?  Thanks

---

### Post by chalex on 2006-12-21
Does it give you an error message?  Does the sound also not work if you run mplayer from the command line?

---

### Post by jdm2 on 2006-12-21
It gives me an error message but I don't know what the command line command is.  

It says on the error message:

Could not open/initialize audio device -> no sound

---

### Post by jdm2 on 2006-12-21
it plays by command line but not when I click the file and tell it to play with mplayer.

here's the command I typed in:

mplayer /media/160drive/Documents/Media/Music/Papercut.mp3

---

### Post by taurus on 2006-12-21
How about (from a terminal)

```
gmplayer /media/160drive/Documents/Media/Music/Papercut.mp3
```
Otherwise, post your ~/.mplayer/gui.conf here...

```
cat ~/.mplayer/gui.conf
```

---

### Post by jdm2 on 2006-12-21
the first command didn't work and I did the second but the file is to big to upload right know.

---

### Post by taurus on 2006-12-21
What's the error message when you run the first command, "gmplayer ........"?

You don't have to upload the whole thing, just the first screen, 24 lines...

---

### Post by hanzomon4 on 2006-12-21
Is mplayer set to use alsa, and how did you set your sound up?.... cause it can be tricky

---

### Post by jdm2 on 2006-12-22
I think it is setup to use alsa or oss.   I used the ubuntu drapper guide to get my sound to work.  Like 2 weekens ago I have somebody help me with my sound becuase it wasn't playing two different things at the same time.  If firefox had a video in it then I couldn't get xms or mplayer to play anything.  What would the 24 line says?  Thanks for the help

---

### Post by taurus on 2006-12-22
```

enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
v_vfm = "ffmpeg"
a_afm = "ffmpeg"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"

```

---

### Post by hanzomon4 on 2006-12-22
> **taurus said:**
> ```

enable_audio_equ = "no"
vo_driver = "xv"
vo_panscan = "0.000000"
vo_doublebuffering = "yes"
vo_direct_render = "no"
vo_dxr3_device = "/dev/em8300-0"
v_framedrop = "0"
v_flip = "0"
v_ni = "no"
v_idx = "-1"
v_vfm = "ffmpeg"
a_afm = "ffmpeg"
vf_pp = "no"
vf_autoq = "0"
vf_lavc = "no"
ao_driver = "alsa"
ao_volnorm = "no"
softvol = "no"
ao_surround = "no"
ao_extra_stereo = "no"
ao_extra_stereo_coefficient = "1.000000"
dvd_device = "/dev/dvd"
cdrom_device = "/dev/cdrom"

```

What is that? A text config for mplayer, never new it had one.........

---

### Post by taurus on 2006-12-22
> **hanzomon4 said:**
> What is that? A text config for mplayer, never new it had one.........

```
more ~/.mplayer/gui.conf
```

---

### Post by jdm2 on 2006-12-22
here is the output for that command.

---

### Post by hanzomon4 on 2006-12-22
It's using oss```
**[_[COLOR="Red"]AO OSS[/COLOR]_] audio_setup: Can't open audio device /dev/dsp: Device or resource busy**

Could not open/initialize audio device ->
``` it should be using alsa.... Here's mine ```
 mplayer /media/MAXTOR/KiN/Music/iTunes/Sonic\ Youth/Sonic\ Nurse/08\ Paper\ Cup\ Exit.mp3 
MPlayer dev-SVN-r21452-4.0.4 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/MAXTOR/KiN/Music/iTunes/Sonic Youth/Sonic Nurse/08 Paper Cup Exit.mp3.
Audio file file format detected.
Clip info:
 Title: Paper Cup Exit
 Artist: Sonic Youth
 Album: Sonic Nurse
 Year: 2004
 Comment: 
 Track: 8
 Genre: Unknown
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Position: 100 %

```

Edit this file ```
gedit ~/.mplayer/gui.conf
``` And change the ao-driver line to this:```
vf_lavc = "no"
**[COLOR="Red"]ao_driver = "alsa"[/COLOR]**
ao_volnorm = "no"
softvol = "yes"

```

EDIT:Removed the unnecessary sudo

---

### Post by taurus on 2006-12-22
> **hanzomon4 said:**
> It's using oss```
**[_[COLOR="Red"]AO OSS[/COLOR]_] audio_setup: Can't open audio device /dev/dsp: Device or resource busy**

Could not open/initialize audio device ->
``` it should be using alsa.... Here's mine ```
 mplayer /media/MAXTOR/KiN/Music/iTunes/Sonic\ Youth/Sonic\ Nurse/08\ Paper\ Cup\ Exit.mp3 
MPlayer dev-SVN-r21452-4.0.4 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/MAXTOR/KiN/Music/iTunes/Sonic Youth/Sonic Nurse/08 Paper Cup Exit.mp3.
Audio file file format detected.
Clip info:
 Title: Paper Cup Exit
 Artist: Sonic Youth
 Album: Sonic Nurse
 Year: 2004
 Comment: 
 Track: 8
 Genre: Unknown
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Position: 100 %

```

Edit this file ```
sudo gedit ~/.mplayer/gui.conf
``` And change the ao-driver line to this:```
vf_lavc = "no"
**[COLOR="Red"]ao_driver = "alsa"[/COLOR]**
ao_volnorm = "no"
softvol = "yes"

```

You don't have to use sudo to edit that file since you are the owner of it!!!  Therefore, this command from a terminal would do just fine...

```
gedit ~/.mplayer/gui.conf
```

---

### Post by hanzomon4 on 2006-12-22
Opps! My bad...... Habit ;)

---

### Post by jdm2 on 2006-12-22
I tried that suggestion and it just made mplayer freeze.  I had to force quite it so it would close.

---

### Post by hanzomon4 on 2006-12-22
Try this ```
mplayer -ao alsa /path/to/file
```

---

### Post by jdm2 on 2006-12-22
windale (Family: 15, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /path/to/file.
File not found: '/path/to/file'
Failed to open /path/to/file


Exiting... (End of file)

---

### Post by hanzomon4 on 2006-12-23
No.... Path/to/file was just me saying "**put the path to the file you want to play**"

---

### Post by jdm2 on 2006-12-24
It doesn't work.  It says it can't do it.

---

