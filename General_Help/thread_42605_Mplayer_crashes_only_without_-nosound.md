---
title: "Mplayer crashes only without -nosound"
date: 2005-06-18
forum: General Help
---

### Post by Hansz on 2005-06-18
I was trying to watch a movie, however.. it doen't work **with** sound :/
I'm using alsa, with the soundcard ens1371.
Other programs such as XMMS/Gaim work perfectly.
With -nosound it works perfectly, here's my output of mplayer(-k6):


MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon Thunderbird (Family: 6, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX



CommandLine:init_freetype
get_path('font/font.desc') -> '/home/hans/.mplayer/font/font.desc'
font: can't open file: /home/hans/.mplayer/font/font.desc
font: can't open file: /usr/share/mplayer/font/font.desc
Using MMX Optimized OnScreenDisplay
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/hans/.mplayer/input.conf'
Can't open input config file /home/hans/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 59 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Setting up LIRC support...
get_path('invfx-sin-ts-xvid-cd2.avi.conf') -> '/home/hans/.mplayer/invfx-sin-ts-xvid-cd2.avi.conf'
Playing invfx-sin-ts-xvid-cd2.avi.
[file] File size is 733671424 bytes
STREAM: [file] invfx-sin-ts-xvid-cd2.avi
STREAM: Description: File
STREAM: Author: Albeu
STREAM: Comment: based on the code from ??? (probably Arpi)
CACHE_PRE_INIT: 0 [0] 0  pre:0  eof:450560  
AVI file format detected.
list_end=0x13A
======= AVI Header =======
us/frame: 40000  (fps=25.000)
max bytes/sec: 0
padding: 0
MainAVIHeader.dwFlags: (272) HAS_INDEX IS_INTERLEAVED
frames  total: 84273   initial: 0
streams: 2
Suggested BufferSize: 0
Size:  640 x 352
==========================
list_end=0xD4
==> Found video stream: 0
====== STREAM Header =====
Type: vids   FCC: xvid (64697678)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 0
Rate: 25/1 = 25.000
Start: 0   Len: 84273
Suggested BufferSize: 75935
Quality 10000
Sample size: 0
==========================
found 'bih', 40 bytes of 40
======= VIDEO Format ======
  biSize 40
  biWidth 640
  biHeight 352
  biPlanes 1
  biBitCount 12
  biCompression 1145656920='XVID'
  biSizeImage 1351680
===========================
Regenerating keyframe table for MPEG4 video
list_end=0x13A
==> Found audio stream: 1
====== STREAM Header =====
Type: auds   FCC:  (0)
Flags: 0
Priority: 0   Language: 0
InitialFrames: 1
Rate: 40000/1 = 40000.000
Start: 0   Len: 134836800
Suggested BufferSize: 20000
Quality -1
Sample size: 1
==========================
found 'wf', 18 bytes of 18
======= WAVE Format =======
Format Tag: 8192 (0x2000)
Channels: 6
Samplerate: 48000
avg byte/sec: 40000
Block align: 1
bits/sample: 0
cbSize: 0
===========================
list_end=0x15E
hdr=Software  size=15
Software  : Nandub v1.0rc2
list_end=0x2B91C9A0
Found movie at 0x80C - 0x2B91C9A0
Reading INDEX block, 168535 chunks for 84273 frames (fpos=0x2b91c9a8)
AVI index offset: 0x808 (movi=0x80C idx0=0x4 idx1=0x4E2C)
Auto-selected AVI audio ID = 1
Auto-selected AVI video ID = 0
AVI: Searching for audio stream (id:1)
AVI video size=594760354 (84273) audio size=134836800 (134836800)
VIDEO:  [XVID]  640x352  12bpp  25.000 fps  1411.5 kbps (172.3 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x352  fps:25.00  ftime:=0.0400
Clip info:
 Software: Nandub v1.0rc2
get_path('sub/') -> '/home/hans/.mplayer/sub/'
get_path('default.sub') -> '/home/hans/.mplayer/default.sub'
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [liba52] AC3 decoding with liba52
dec_audio: Allocating 3840 bytes for input buffer.
dec_audio: Allocating 6144 + 65536 = 71680 bytes for output buffer.
AC3: 5.1 (3f+2r+lfe)  48000 Hz  320.0 kbit/s
A52 flags before a52_frame: 0x2A
A52 flags after a52_frame: 0xA
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 40000->192000 (320.0 kbit)
Selected audio codec: [a52] afm:liba52 (AC3-liba52)
==========================================================================
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports layers.
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours LAYER FULLSCREEN ABOVE BELOW X atoms
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
INFO: libavcodec init OK!
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
[libaf] Adding filter dummy 
[dummy] Was reinitialized, rate=48000Hz, nch = 2, format = 0x00000001 and bps = 2
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int 
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: requested format: 48000 Hz, 2 channels, Signed 16-bit (Little-Endian)
alsa-init: compiled for ALSA-1.0.8
alsa-init: setup for 1/2 channel(s)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
alsa-init: pcm opend in block-mode
alsa-init: chunksize set to 1024
alsa-init: fragcount=16
alsa-init: got buffersize=65536
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
AO: Description: ALSA-0.9.x-1.x audio output
AO: Author: Alex Beregszaszi, Zsolt Barat <joy@streamminister.de>
AO: Comment: under developement
Building audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
[dummy] Was reinitialized, rate=48000Hz, nch = 2, format = 0x00000001 and bps = 2
[dummy] Was reinitialized, rate=48000Hz, nch = 2, format = 0x00000001 and bps = 2
Starting playback...
alsa-space: free space = 65536, prepared --
Uninit audio filters...
[libaf] Removing filter dummy 
uninit audio: liba52
uninit video: ffmpeg
alsa-uninit: pcm closed
vo: uninit ...

---

