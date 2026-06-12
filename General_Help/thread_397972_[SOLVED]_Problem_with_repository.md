---
title: "[SOLVED] Problem with repository"
date: 2007-03-31
forum: General Help
---

### Post by Hutom on 2007-03-31
I was trying to install mplayer, which I didn't find in package manager in spite of having all repositories enabled. I tried to re enable it through the software sources tab.   Following error occurred --

"[COLOR="Red"]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference.[/COLOR] "

I tried to check my source list. Typed "[COLOR="Red"]cat /etc/apt/sources.list[/COLOR]" in the terminal. Following reply came --

> #
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
#AUTOMATIX REPOS END

I tried to remove AUTOMATIX. Now my add/remove is not working. It says,

[COLOR="Red"]This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]

So, what should I do now?

---

### Post by taurus on 2007-03-31
Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Hutom on 2007-03-31
Thanks. Problem resolved. I just put some # before some malformed lines. Things are otherwise working fine. Only I still cannot play a vcd. totem, vlc, mplayer nothing is working.

---

### Post by Shmifty on 2007-03-31
Make sure you have the codecs for the players installed or else nothing will play.

---

### Post by Hutom on 2007-03-31
What codec? Can you give me a link please.

---

### Post by Hutom on 2007-03-31
By the way, can AUTOMATIX create a problem?

---

### Post by Shmifty on 2007-03-31
There is an edit feature on this site (just for future reference).

I use automatix and I don't have any problems, I just suggest that you only use it for programs aptitude/adept/synaptic have trouble dealing with.

install w32codecs and you should be able to play most everything.

---

### Post by taurus on 2007-03-31
> **Hutom said:**
> What codec? Can you give me a link please.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help. 

Let me firmly reiterate that Automatix is just as it is -- 

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by Hutom on 2007-04-01
Well, I am very new to linux (only 4-5 days back I installed it and started learning it) and I hope you guys won't mind if I ask few questions to clear my doubts. 

1)  Taurus and Shmifty says I need w32codecs. Well this 'w' always makes me skeptical. Is it related to 'WINDOWS'? If yes then why should I install it?

2) Taurus  has provided a link. As the community document asks, I already have all repositories enabled. However, I don't know whether I already have this w32codec installed. The community document talks about support for restricted formats. But it never said anything particularly about w32codec. It never mentioned a place from which  I can download this particular codec. If I download and install something I want to know exactly what I am downloading. If I need this particular codec then why should I download a big package of which this codec will just be a part? Is there a way that I can see which codec I need and then download and install that particular codec?

3) To Compiledkernel:
Well, people learn from mistakes. I already have this AUTOMATIX installed. Honestly it has not given me any serious trouble so far. However I shall be more careful in future.

[COLOR="Red"]Now I still can't play vcd (mpeg files) in either vlc or mplaye[/COLOR]r. So, here is something I tried,

I typed "[COLOR="Red"] mplayer /cdrom/MPEGAV/AVSEQ01.DAT[/COLOR]" in terminal. This is the reply,

> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


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

Playing /cdrom/MPEGAV/AVSEQ01.DAT.
Seek failed

Then I typed, "[COLOR="Red"] mplayer vcd://[/COLOR]". Reply is this,

> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


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

Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:21:21  mode: 3
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1100.0 kbps (137.5 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x288 => 376x288 Planar YV12 
V:   0.0   1/  1 ??% ??% ??,?% 0 0 

Exiting... (End of file)


Anyone has any idea about what went wrong?

---

### Post by zvacet on 2007-04-01
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs
```
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

---

### Post by Hutom on 2007-04-02
Thank you zvacet. Installed them. However, still can't play a vcd. 
This is the reply when I typed ," mplayer -v -identify vcd://"

> MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


get_path('codecs.conf') -> '/home/taposik/.mplayer/codecs.conf'
Reading /home/taposik/.mplayer/codecs.conf: Can't open '/home/taposik/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
CommandLine: '-v' '-identify' 'vcd://'
init_freetype
get_path('font/font.desc') -> '/home/taposik/.mplayer/font/font.desc'
font: can't open file: /home/taposik/.mplayer/font/font.desc
Font /usr/share/mplayer/font/font.desc loaded successfully! (206 chars)
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Using nanosleep() timing
get_path('input.conf') -> '/home/taposik/.mplayer/input.conf'
Can't open input config file /home/taposik/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 60 binds
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
get_path('.conf') -> '/home/taposik/.mplayer/.conf'

Playing vcd://.
get_path('sub/') -> '/home/taposik/.mplayer/sub/'
ID_VCD_START_TRACK=1
ID_VCD_END_TRACK=2
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 3
track 02:  adr=1  ctrl=4  format=2  00:21:21  mode: 3
ID_VCD_TRACK_1_MSF=00:19:21
ID_VCD_TRACK_2_MSF=43:47:10
VCD start byte position: 0x551B8  end: 0x3898B0
STREAM: [vcd] vcd://
STREAM: Description: Video CD
STREAM: Author: Albeu
STREAM: Comment: based on the code from ???
Checking for YUV4MPEG2
ASF_check: not ASF guid!
Checking for NuppelVideo
Checking for REAL
Checking for SMJPEG
Searching demuxer type for filename vcd:// ext: (null)
Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
header block 1 size: 0
stream_seek: WARNING! Can't seek to 0x4 !
AVS: avs_check_file - attempting to open file vcd://
AVS: File is too big, aborting...
Checking for PVA
Checking for MPEG-TS...
THIS DOESN'T LOOK LIKE AN MPEG-TS FILE!
TRIED UP TO POSITION 404313, FOUND 0, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=0 size=-8
LMLM4 Stream Format not found
system stream synced at 0xD4C57 (871511)!
==> Found video stream: 1
ID_VIDEO_ID=1
  {ERROR5,c=85}  
  {ERROR5,c=85}  
  {ERROR5,c=208}  
  {ERROR5,c=85}  
  {ERROR5,c=12}  
  {PTS_err:1}  
==> Found video stream: 0
ID_VIDEO_ID=0
  {PTS_err:1}  
==> Found video stream: 6
ID_VIDEO_ID=6
  {ERROR5,c=88}  
  {ERROR5,c=2}  
  {ERROR5,c=2}  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
stream_seek: WARNING! Can't seek to 0x30F790 !
MPEG-PS file format detected.
  {ERROR5,c=85}  
  {ERROR5,c=85}  
  {ERROR5,c=208}  
  {ERROR5,c=85}  
  {ERROR5,c=12}  
  {PTS_err:1}  
  {PTS_err:1}  
  {ERROR5,c=88}  
  {ERROR5,c=2}  
  {ERROR5,c=2}  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: audio)  
MPEG: No audio stream found -> no sound.
Searching for sequence header... OK!
VIDEO:  MPEG1  352x288  (aspect 8)  25.000 fps  1100.0 kbps (137.5 kbyte/s)
[V] filefmt:2  fourcc:0x10000001  size:352x288  fps:25.00  ftime:=0.0400
get_path('sub/') -> '/home/taposik/.mplayer/sub/'
ID_FILENAME=vcd://
ID_DEMUXER=mpegps
ID_VIDEO_FORMAT=0x10000001
ID_VIDEO_BITRATE=1100000
ID_VIDEO_WIDTH=352
ID_VIDEO_HEIGHT=288
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_LENGTH=0.00
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
X11 opening display: :0.0
vo: X11 color mask:  FFFFFF  (R:FF0000 G:FF00 B:FF)
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
[x11] Detected wm supports NetWM.
[x11] Detected wm supports FULLSCREEN state.
[x11] Detected wm supports ABOVE state.
[x11] Detected wm supports BELOW state.
[x11] Current fstype setting honours FULLSCREEN ABOVE BELOW X atoms
[xv common] Drawing colorkey manually.
[xv common] Using colorkey from Xv (0x000821).
[xv common] Maximum source image dimensions: 1920x1200
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 288 (preferred colorspace: Mpeg PES)
Trying filter chain: vo
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
SwScale params: -1 x -1 (-1=no scaling)
Trying filter chain: scale vo
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
ID_VIDEO_CODEC=mpeg12
Audio: no sound
Freeing 0 unused audio chunks.
Starting playback...
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
Trying filter chain: vo
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO Config (352x288->376x288,flags=0,'MPlayer',0x32315659)
VO: [xv] 352x288 => 376x288 Planar YV12 
VO: Description: X11/Xv
VO: Author: Gerd Knorr <kraxel@goldbach.in-berlin.de> and others
Xvideo image format: 0x32595559 (YUY2) packed
Xvideo image format: 0x32315659 (YV12) planar
Xvideo image format: 0x434d5658 (XVMC) planar
Xvideo image format: 0x35315652 (RV15) packed
Xvideo image format: 0x36315652 (RV16) packed
Xvideo image format: 0x32335652 (RV32) packed
using Xvideo port 68 for hw scaling
[xv] dx: 0 dy: 0 dw: 376 dh: 288
*** [vo] Allocating mp_image_t, 352x288x12bpp YUV planar, 152064 bytes
[xv] dx: 0 dy: 0 dw: 376 dh: 288
MPEG Stream reached EOF% ??,?% 0 0 
ds_fill_buffer: EOF reached (stream: video)  
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
EOF code: 1    1 ??% ??% ??,?% 0 0 

Uninit video: libmpeg2
vo: uninit ...

Exiting... (End of file)

---

### Post by Hutom on 2007-04-02
Guys, here is something interesting. 
 "mplayer -vo x11 vcd://2" is working. However it is not showing the options menu. I cannot full screen it. cannot increase the sound, nothing. I think a little more effort and the problem can be resolved.

---

### Post by zvacet on 2007-04-02
**Preferences>codecs&demuxer>FFmpeg/libavcodec audio decoders**
Maybe some other will work for you,so try out.

---

### Post by Hutom on 2007-04-02
> **zvacet said:**
> **Preferences>codecs&demuxer>FFmpeg/libavcodec audio decoders**
Maybe some other will work for you,so try out.

Any other way to install these decoders?

---

### Post by Hutom on 2007-04-02
**[COLOR="Red"]Sorry, my mistake. Please ignore my last post.[/COLOR]**

---

