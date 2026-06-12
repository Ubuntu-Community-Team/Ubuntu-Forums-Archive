---
title: "Mplayer and cinelerra problems"
date: 2005-04-11
forum: General Help
---

### Post by ossi on 2005-04-11
Hi!

Yesterday I upgraded to hoary. So far anything works fine, except the video player support for Mplayer and cinelerra. The videoplayback works in totem and xine.

Before updating to hoary Mplayer worked. When I start Mplayer by using xterm the following message appears:

ossi@asus:~/data/videos $ mplayer ndn-kl.mpg
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 6)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



73 audio & 180 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing ndn-kl.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25,000 fps  1200,0 kbps (150,0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 16000->192000 (128,0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default


MPlayer interrupted by signal 2 in module: enable_cache


MPlayer interrupted by signal 2 in module: ao2_init
ossi@asus:~/data/videos $ mplayer -vo xv -vop yuy2 ndn-kl.mpg
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 6)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



73 audio & 180 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing ndn-kl.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x288  (aspect 8)  25,000 fps  1200,0 kbps (150,0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 16000->192000 (128,0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
Opening video filter: [yuy2]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default


MPlayer interrupted by signal 2 in module: enable_cache


MPlayer interrupted by signal 2 in module: ao2_init

----------------------------------------------------------------------------

Has it got something to do with xorg? Has got anyone installed cinelerra and if yes, how can that problem be solved?

greetings, ossi

---

### Post by fsman on 2005-04-11
has anyone got cinelerra in hoary? if so how?

---

### Post by ossi on 2005-04-12
You got to add the source manually. Thats not the problem. But I tried a bit again today and I am quite sure that this has got something to do with xorg. It is not possible to playback the material. But not only videos, also mp3s. Does anybody know more about it?

---

