---
title: "Broken video in Totem and Mplayer"
date: 2007-12-13
forum: General Help
---

### Post by reader4 on 2007-12-13
Strange situation... videos had been working fine on my 64-bit Gutsy desktop, NVIDIA.  Today, when I tried to play a video in either Totem or Mplayer, I get the same result: a scrambled mess.  It doesn't matter what type of video: MPG1, MPG2, MP4, DV, AVI, WMV, FLV, etc. - they all have the same problem as shown in this capture:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=53109&stc=1&d=1197560492[/IMG]

```
$ totem --debug sample.mpg
init class succeeded
gnome_vfs init_input_class
params.c:OpenConfFile() - Unable to open configuration file "/home/user/.smb/smb.conf":
        No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/user/.smb/smb.conf.append":
        No such file or directory
Using netbios name NETBIOS.
Using workgroup WORKGROUP.
video_out_xv: using Xv port 500 from adaptor NV17 Video Texture for hardware colorspace conversion and scaling.
video_out_xv: this adaptor supports the yuy2 format.
video_out_xv: this adaptor supports the yv12 format.
x11osd: unscaled overlay created (XShape mode).
video_out: thread created
audio_alsa_out : supported modes are 8bit 16bit 24bit mono stereo (4-channel not enabled in xine config) (4.1-channel not enabled in xine config) (5-channel not enabled in xine config) (5.1-channel not enabled in xine config) (a/52 and DTS pass-through not enabled in xine config)
audio_out: thread created
xine_stream_new
load_plugins: no post plugin named GOOM: what a GOOM! found
video_out_xv: VO_PROP_INTERLACED(0)
libsputext: spu_src_encoding = utf-8
video_out_xv: VO_PROP_ZOOM_X = 100
video_out_xv: VO_PROP_ZOOM_Y = 100
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'image'
load_plugins: probing demux 'real'
load_plugins: probing demux 'quicktime'
load_plugins: probing demux 'ogg'
load_plugins: probing demux 'fli'
load_plugins: probing demux 'slave'
load_plugins: probing demux 'yuv4mpeg2'
load_plugins: probing demux 'flashvideo'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'nsf'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'tta'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'matroska'
ebml: invalid EBML ID size (0x0) at position 1
ebml: invalid master element
load_plugins: probing demux 'nsv'
load_plugins: probing demux 'mpeg_block'
load_plugins: probing demux 'mpeg_pes'
load_plugins: probing demux 'avi'
load_plugins: probing demux 'mng'
load_plugins: probing demux 'iff'
load_plugins: probing demux 'wve'
load_plugins: probing demux 'idcin'
load_plugins: probing demux 'ipmovie'
load_plugins: probing demux 'vqa'
load_plugins: probing demux 'wc3movie'
load_plugins: probing demux 'roq'
load_plugins: probing demux 'str'
load_plugins: probing demux 'film'
load_plugins: probing demux 'smjpeg'
load_plugins: probing demux 'fourxm'
load_plugins: probing demux 'vmd'
load_plugins: probing demux 'asf'
load_plugins: probing demux 'pva'
load_plugins: probing demux 'mpeg-ts'
load_plugins: probing demux 'mpeg'
xine: found demuxer plugin: MPEG program stream demux plugin
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 33190
load_plugins: plugin dxr3-mpeg2 failed to instantiate itself.
load_plugins: plugin mpeg2 will be used for video streamtype 00.
load_plugins: plugin mad will be used for audio streamtype 01.
audio_alsa_out: audio rate : 44100 requested, 48000 provided by device/sec
audio_alsa_out:open pause_resume=0
output sample rate 48000
will resample audio from 44100 to 48000
ao_close
xine_play
video discontinuity #2, type is 2, disc_off 69963
waiting for audio discontinuity #2
audio discontinuity #2, type is 2, disc_off 69963
waiting for in_discontinuity update #2
audio jump, diff=0
AFD changed from -2 to -1
video jump
play_internal ...done
fixing sound card drift by -2383 pts
fixing sound card drift by -1785 pts
fixing sound card drift by -1338 pts
video_out: throwing away image with pts 923184 because it's too old (diff : 28285).
video_out: throwing away image with pts 926187 because it's too old (diff : 25282).
video_out: throwing away image with pts 929190 because it's too old (diff : 22279).
video_out: throwing away image with pts 932193 because it's too old (diff : 19276).
video_out: throwing away image with pts 935196 because it's too old (diff : 16273).
video_out: throwing away image with pts 938199 because it's too old (diff : 13270).
video_out: throwing away image with pts 941202 because it's too old (diff : 10267).
video_out: throwing away image with pts 944205 because it's too old (diff : 7264).
video_out: throwing away image with pts 947208 because it's too old (diff : 4261).
video_out: throwing away image with pts 1136397 because it's too old (diff : 8149).
video_out: throwing away image with pts 1139400 because it's too old (diff : 5146).
200 frames delivered, 2 frames skipped, 11 frames discarded
video_out: throwing away image with pts 2358609 because it's too old (diff : 4395).
200 frames delivered, 0 frames skipped, 1 frames discarded
ao_flush (loop running: 1)
input_cache: read calls: 51488, main input read calls: 5828
input_cache: seek_calls: 70, main input seek calls: 10
video_out_xv: VO_PROP_ZOOM_X = 100
video_out_xv: VO_PROP_ZOOM_Y = 100
gnome_vfs init_input_class
xine: found input plugin  : file input plugin
load_plugins: probing demux 'anx'
load_plugins: probing demux 'image'
load_plugins: probing demux 'real'
load_plugins: probing demux 'quicktime'
load_plugins: probing demux 'ogg'
load_plugins: probing demux 'fli'
load_plugins: probing demux 'slave'
load_plugins: probing demux 'yuv4mpeg2'
load_plugins: probing demux 'flashvideo'
load_plugins: probing demux 'aud'
load_plugins: probing demux 'aiff'
load_plugins: probing demux 'flac'
load_plugins: probing demux 'nsf'
load_plugins: probing demux 'realaudio'
load_plugins: probing demux 'snd'
load_plugins: probing demux 'tta'
load_plugins: probing demux 'voc'
load_plugins: probing demux 'vox'
load_plugins: probing demux 'mod'
TEST mod decode
load_plugins: probing demux 'matroska'
ebml: invalid EBML ID size (0x0) at position 1
ebml: invalid master element
load_plugins: probing demux 'nsv'
load_plugins: probing demux 'mpeg_block'
load_plugins: probing demux 'mpeg_pes'
load_plugins: probing demux 'avi'
load_plugins: probing demux 'mng'
load_plugins: probing demux 'iff'
load_plugins: probing demux 'wve'
load_plugins: probing demux 'idcin'
load_plugins: probing demux 'ipmovie'
load_plugins: probing demux 'vqa'
load_plugins: probing demux 'wc3movie'
load_plugins: probing demux 'roq'
load_plugins: probing demux 'str'
load_plugins: probing demux 'film'
load_plugins: probing demux 'smjpeg'
load_plugins: probing demux 'fourxm'
load_plugins: probing demux 'vmd'
load_plugins: probing demux 'asf'
load_plugins: probing demux 'pva'
load_plugins: probing demux 'mpeg-ts'
load_plugins: probing demux 'mpeg'
xine: found demuxer plugin: MPEG program stream demux plugin
video discontinuity #3, type is 0, disc_off 0
waiting for audio discontinuity #3
ao_close
audio_out: no streams left, closing driver
audio discontinuity #3, type is 0, disc_off 0
waiting for in_discontinuity update #3
vpts adjusted with prebuffer to 3409574
load_plugins: plugin mpeg2 will be used for video streamtype 00.
load_plugins: plugin mad will be used for audio streamtype 01.
audio_alsa_out: audio rate : 44100 requested, 48000 provided by device/sec
audio_alsa_out:open pause_resume=0
output sample rate 48000
will resample audio from 44100 to 48000
set_speed 0
audio_alsa_out: Drain call failed. (err=-11:Resource temporarily unavailable)
input_cache: read calls: 1255, main input read calls: 157
input_cache: seek_calls: 68, main input seek calls: 8
xine_dispose
shutdown audio
ao_close
audio_out: no streams left, closing driver
shutdown video
xine_exit: bye!

```

```
$ mplayer sample.mpg
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Xeon(TM) CPU 3.40GHz (Family: 15, Model: 4, Stepping: 3)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing sample.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG1  352x240  (aspect 12)  29.970 fps  1150.0 kbps (143.8 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 499.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 352 x 240 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 224.0 kbit/15.87% (ratio: 28000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 352 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.30:1 - prescaling to correct movie aspect.
VO: [xv] 352x240 => 352x270 Planar YV12 
Cannot sync MAD frame:  0.009 ct: -0.029 1114/1114  1%  0%  1.7% 0 0 
Cannot sync MAD frame
Cannot sync MAD frame:  0.008 ct: -0.029 1115/1115  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.011 ct: -0.028 1116/1116  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.010 ct: -0.028 1117/1117  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.008 ct: -0.028 1118/1118  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.011 ct: -0.027 1119/1119  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.010 ct: -0.027 1120/1120  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.008 ct: -0.026 1121/1121  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.011 ct: -0.026 1122/1122  1%  0%  1.7% 0 0 
Cannot sync MAD frame:  0.009 ct: -0.025 1123/1123  1%  0%  1.7% 0 0 
Cannot sync MAD frame: -0.011 ct: -0.027 1124/1124  1%  0%  1.7% 0 0 
A:  38.2 V:  38.2 A-V: -0.011 ct: -0.029 1124/1124  1%  0%  1.7% 0 0 
GNOME screensaver enabled

Exiting... (End of file)

```

Any ideas what might be going on?  I have a gutsy laptop that is mostly sync'd to this desktop and plays everything just fine.  I have a feeling a restart could help, but I am running simulations in the background that take hours-days to finish, so restarting is not an option at this point.

---

### Post by reader4 on 2007-12-14
Update: I was able to restart the computer today and everything works again.  I would love to figure out what caused this problem and what process needed to be restarted so I could potentially avoid a full system restart again.

---

### Post by reader4 on 2008-02-22
Anyone else having this issue?  I haven't done a lot of work on this, but it seems to be a problem after playing some FLV videos.  Suddenly, nothing will play... everything looks like this:  

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=60423&stc=1&d=1203700151[/IMG]

---

### Post by Maverickprowls on 2008-03-01
I have a similar problem, the video is completely scrambled in ALL my media players, and that applies to Realplayer, Totem, Mplayer, vlc. Just as with the above poster's problem, the video is scrambled irrespective of the format, and the problem seems to clear on reboot, but then comes back unexpectedly.  Sometimes it has been known to clear if I stop running programs under wine, but this is not always the case.

My video output looks like this 
[[IMG]http://www.maybeoneday.org.uk/images/Screenshot-9-thumb.png[/IMG]](http://www.maybeoneday.org.uk/images/Screenshot-9.png)

as you can see from the background, mplayer seems to be working fine, but the output generated is a mess.

---

### Post by mredub on 2008-03-26
Same issue here (exactly)  attached of what mine looks like...   a <CTRL>-ALT <BKSP> will fix it, so will a reboot.

my machine is an older athlon XP-M 2500 (in a desktop) Shuttle Nforce 2 Mobo with a Ndivia 6600GT video card.


it happend fairly regularly like every few days if i'm watching videos.  is there a bug listed somewhere to track the issue?

---

### Post by JerMe on 2008-03-28
Same problem here... I just did a fresh install of Gutsy and I'm getting the same scrambled picture every once in a while.  A reboot or ctrl+alt+backspace will fix it.  Seems like an graphics driver issue?

---

### Post by Maverickprowls on 2008-03-30
I now have the additional problem that this video disruption starts spontaneously, whereas before it seemed only to occur after I ran programs under wine.  

Any help or suggestions for problem diagnosis would be greatly appreciated.

---

### Post by Pietro Pizzi on 2008-04-03
same problem, all formats on all players, mostly when i run wine, sometimes it's ok with wine and sometimes i comes without wine.

reeboot, kill X11 helps and when it comes from wine offten it goes when i close the wine app.

my sys: after i had updatet my machine from the first ubuntu i decidet to do a fresh install 2 weaks ago. so all is fresh and clean, i use kubuntu 7.10.

is there any help at the moment?

---

### Post by lewac on 2008-04-05
well one thing I've found poking around in these various distro's is that ubuntu just doesn't seem to "like" ATI for some reason. probably like a lot of us we're trying ubuntu out on our windoze boxes via a dual boot via grub. simple to do so why not try it, right?

well I've been running across some of these boxes that sport at least one ATI card. thus one solution is to ascertain that you're running some flavor of nvidea and that if you have more than one video card installed to the box also ascertain that the cards match (for example AGP AND PCI installed to the same box could very well give some rather strange behaviour... which may not be limited to only video issues). I've seen mouse freezes, etc. 

and not only that but when some of these systems are initially configured NO such anomalies appear. but as the system in question "ages" thingee's appear to begin to go amiss! so sometimes a cigar is simply a cigar or in essence check the hardware FIRST when strange anomalies appear! another thing to be mindful of is your video BIOS settings. if they're not set properly all types of weird happenings may occur.

---

### Post by Pietro Pizzi on 2008-04-08
this problem must have another reason. i have only one nvidia 6600gt in pci-e. and bevor i installed gutsy all was pretty fine.

i have figured out that a restart isn't necessary, it is enough to log out and in from kde, without kill/restart kdm or X11. for additional info, in dmesg or  /var/log/messages for example i can't see anything special.

---

### Post by ornotermes on 2008-04-13
Well, i have the same problem, and it seems to be linked to the video output module rather than hardware, and on my system i have only notified the bug if i have played steam and started a movie without exit steam first. I'm not sure if the problem occurs only by having some wine processes running or if it happens only when wine applications is on the desktop. If i exit steam before starting movie it often play normal.

---

### Post by Maverickprowls on 2008-04-13
I would dearly like to try and work out exactly what is broken in my video output system.  There are several factors that I think might be helpful to anyone with more technical knowledge out there.

- I can still generate thumbnails (even for files newly arrived on the system) whilst my video output is scrambled
- On my system at least, a Ctrl-Del-Backspace *doesn't* fix the problem, I have to do a complete reboot ( I use Ubuntu 7.10 and a Gnome desktop)
- My system doesn't like Compiz in the least, so I have the low-fi desktop without additional effects (My hardware would appear to be up to the job, Compiz crashes too often to be usable to me, or I lose important parts of my window, like the frame and buttons)
- When running any of the media/video apps from the command-line to view console output (vlc, mplayer, etc), there does not appear to be anything wrong with their outputs.
- Video from internet sources such as YouTube works fine when my Video is screwed up, I can't say whether this is relevant.

Does anyone have any hints?  Or could someone at least point me in the right direction so I can work out what's broken.

---

### Post by sawdust_prophet on 2008-04-13
This wasn't an issue for me at first, but it is now.  It doesn't seem to be linked to use of Wine, just at some point video goes scrambled, but I still get thumbnails etc, all the usual symptoms already listed.  Running Ubuntu 7.10, GNOME, Athlon 2100+ 1.5 GB RAM GeForce 6600.

Would be nice if someone could figure this out :/

---

### Post by kerryhall on 2008-04-16
Bump. I have the exact same problem. It happens even when I just have Totem running, and appears to be random. My video card is a geforce 6600 GT PCIE.

Thanks all!

---

### Post by ornotermes on 2008-04-18
Well, i have a NV 6600 GT and many others seems to have that too, is there anyone that does not have 6600 but suffer from these video bugs?

---

### Post by Pietro Pizzi on 2008-04-28
I upgradet to hardy and the Problem with (no)vid and wine is gone for me!

---

### Post by reader4 on 2008-05-01
Nvidia GeForce 1400 here.  I have exact same OS install on a laptop with integrated graphics and never had a problem.  I haven't upgraded to Hardy yet, but the problem definitely seems to be related to leaving a video before it ends (particularly FLV) and then trying another.  Sort of glad to hear I'm not the only one... anyone else upgrade to Hardy still having issues?

---

### Post by Maverickprowls on 2008-05-01
I upgraded to HH a couple of days ago and *so far* I'm happy to report no video problems.  

(An aside - It did renumber all my devices in fstab, though, watch out for that if you're upgrading)

---

