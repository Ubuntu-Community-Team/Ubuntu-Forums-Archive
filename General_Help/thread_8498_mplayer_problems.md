---
title: "mplayer problems"
date: 2004-12-17
forum: General Help
---

### Post by bob k on 2004-12-17
Resolved:
I added quiet = yes  to the config file
I missed this in the FAQ.
It really doesn't say this in the FAQ, they have as a command line option -quiet, but from I've seen most of the command line options can be placed in the config file in this format.

I installed mplayer a couple weeks ago and it works fairly good. I was going through my xsession-errors log to clean-up any install problems.

When ever I play a mpeg with filefox I get the following entries in my log file.

Playing /tmp/001.mpg.

Cache fill:  5.72% (479996 bytes)    MPEG-PS file format detected.
VIDEO:  MPEG1  240x160  (aspect 1)  24.000 fps  307.2 kbps (38.4 kbyte/s)
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
MP3lib: init layer2&3 finished, tables done
AUDIO: 32000 Hz, 2 ch, 16 bit (0x10), ratio: 8000->128000 (64.0 kbit)
Selected audio codec: [mp3] afm:mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/devices.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 240 x 160 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.3.1
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG 1 or 2 (libmpeg2))
==========================================================================
Checking audio filter chain for 32000Hz/2ch/16bit -> 32000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 32000 hz, little endian signed int 
AF_pre: 32000Hz 2ch Signed 16-bit (Little-Endian)
AO: [oss] 32000Hz 2ch Signed 16-bit (Little-Endian) (2 bps)
Building audio filter chain for 32000Hz/2ch/16bit -> 32000Hz/2ch/16bit...
Starting playback...
VDec: vo config request - 240 x 160 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 240x160 => 240x160 Planar YV12  [fs] [zoom]
SwScaler: using unscaled Planar YV12 -> BGR 32-bit special converter
A:   0.4 V:   0.0 A-V:  0.324 ct:  0.000    1/  1   0%  0%  0.0% 0 0 5%
A:   0.4 V:   0.2 A-V:  0.215 ct:  0.004    2/  2   0%  0%  0.0% 0 0 5%
A:   0.6 V:   0.3 A-V:  0.333 ct:  0.008    3/  3   0%  0%  0.0% 0 0 5%
A:   0.6 V:   0.3 A-V:  0.292 ct:  0.013    4/  4   0%  0%  0.0% 1 0 5%
A:   0.6 V:   0.3 A-V:  0.252 ct:  0.017    5/  5   0% 

The last part of this will continue until it overloads the log buffer. Looking at the log buffer it says that I dont have an Xvideo codec and associted error there after, but the clip plays fine. Since this error hoses my xsession file and most prob affects play back I would like to fix this. Below is my .mplayer/config file. Anybody have any ideas?

Tia
Bob

##
## MPlayer config file
##
## This file can be copied to /usr/local/etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /usr/local/etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

#vo=x11			# To specify default video driver (see -vo help for
			# list)

#ao=oss			# To specify default audio driver (see -ao help for
			# list)

fs=yes			# Enlarges movie window to your desktop's size.
			# Used by drivers: all

#vm=yes			# Tries to change to a different videomode
			# Used by drivers: dga2, x11, sdl

bpp=24			# Force changing display depth.
			# Valid settings are: 0, 15, 16, 24, 32
			# may need 'vm=yes' too.
			# Used by drivers: fbdev, dga2, svga, vesa

zoom=yes		# Enable software scaling (powerful CPU needed)
			# Used by drivers: svga, x11, vesa

double=yes		# use double-buffering (recommended for xv with
			# SUB/OSD usage)

# monitoraspect=4:3	# standard monitor size, with square pixels
# monitoraspect=16:9	# use this for widescreen monitor! non-square pixels

# ontop=yes		# Makes the player window stay ontop
			# Used by drivers which use X11, except SDL,
			# as well as directx and gl2 under Windows

##
## Specify your preferred default skin here
## (skins are searched in /usr/local/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default

##
## Multiple languages are available :)
##
## Hungarian	igen	nem
## English	yes	no
## German	ja	nein
## Spanish	si	no
## Polish	tak	nie
## Swedish ja nej
## Binary	1	0
##
## You can also use spaces and/or tabs.
##

# sound		= 1
# nosound	= nein
mixer		= /dev/mixer

##
## resample the fonts' alphamap
## 0	plain white fonts
## 0.75	very narrow black outline (default)
## 1	narrow black outline
## 10	bold black outline
##

# ffactor = 0.75

##
## FBdev driver: 

# fb = /dev/fb0				# framebuffer device to use
# fbmode = 640x480-120			# use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes		# the fb.modes file

## VESA and FBdev driver: specify your monitor's timings
## 
## (see for example /etc/X11/XF86Config for timings!)
## ** CAUTION! IF YOUR DISPLAY DOESN'T SUPPORT AUTOMATICALLY TURNING OFF WHEN
##    OVERDRIVED (AND EVEN IF IT DOES), THIS MAY CAUSE DAMAGE TO YOUR DISPLAY!
##    WE AREN'T RESPONSIBLE, IT'S YOUR DECISION! **
##
## k, K : means multiply by 1000
## m, M : means multiply by 1.000.000
##
 monitor-hfreq = 31.5k-80k		# horizontal frequency range
 monitor-vfreq = 60-75			# vertical frequency range
# monitor-dotclock = 30M-300M		# dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib	# use SDL video driver by default
			# use "vo = sdl:aalib" or "vo sdl:dga" and so on,
			# for specifying SDL subdrivers
# ao = sdl:esd		# use SDL audio driver by default
			# use "ao = sdl:esd" to use SDL's ESD driver
xv = no		        # whether to use XVideo hardware acceleration or not
# forcexv = yes		# force XVideo even if not detected


##
## Other (preferred to be default from configfile) switches
##

framedrop 	= yes	# drop frames, when not in sync (slow CPU, videocard,
			# etc)

cache		= 8192	# use 8Mb input cache by default

# slang		= en	# DVD : display english subtitles if available
alang		= en	# DVD : play english audio tracks if available
loop		= 0


## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

##
## You can also include other configfiles
## Specify full path!
##
## Delete this default :)
##

#include = /home/gabucino/.mplayer/i_did_not_RTFM_carefully_enough...

---

