---
title: "still more mplayer"
date: 2005-10-10
forum: General Help
---

### Post by ppioneer on 2005-10-10
i originally tried apt-get the mplayer and mplayer plugin and they didnt work so i removed them and built from source. now my problem is mplayer plugin buffers to 99% and just hangs, ive read all 14 pages of mplayer related posts and none proved helpful. my confs follow

mplayer.conf

##
## MPlayer config file
##
## This file can be copied to /etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=x11,                 # To specify default video driver (see -vo help for
                        # list)

ao=alsa,                # To specify default audio driver (see -ao help for
                        # list)

fs=no                   # Enlarges movie window to your desktop's size.
                        # Used by drivers: all

vm=no                   # Tries to change to a different videomode
                        # Used by drivers: dga2, x11, sdl

bpp=0                   # Force changing display depth.
                        # Valid settings are: 0, 15, 16, 24, 32
                        # may need 'vm=yes' too.
                        # Used by drivers: fbdev, dga2, svga

zoom=no                 # Enable software scaling (powerful CPU needed)
                        # Used by drivers: svga, aalib

double=yes              # use double-buffering (recommended for xv with
                        # SUB/OSD usage)

# x=800                 # scale movie to <x> pixels width
# y=600                 # scale movie to <y> pixels height

osdlevel=1              # don't display OSD at stratup

monitoraspect=4:3       # standard monitor size, with square pixels
# monitoraspect=16:9    # use this for widescreen monitor! non-square pixels

cache = 1024            # Disk cache 1 MB

##
## Specify your preferred default skin here
## (skins are searched in /usr/share/mplayer/Skin/yourskin
##  and ~/.mplayer/Skin/yourskin)
##

skin = default


##
## Multiple languages are available :)
##
## Hungarian    igen    nem
## English      yes     no
## German       ja      nein
## Spanish      si      no
## Binary       1       0
##
## You can also use spaces and/or tabs.
##

#sound          = 1
#nosound        = nein
#mixer          = /dev/mixer

##
## resample the fonts' alphamap
## 0    plain white fonts
## 0.75 very narrow black outline (default)
## 1    narrow black outline
## 10   bold black outline
##

#ffactor = 0.75

##
## FBdev driver:

# fb = /dev/fb0                         # framebuffer device to use
# fbmode = 640x480-120                  # use this mode (read from fb.modes!)
# fbmodeconfig = /etc/fb.modes          # the fb.modes file

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
# monitor_hfreq = 31.5k-50k,70k         # horizontal frequency range
# monitor_vfreq = 50-90                 # vertical frequency range
# monitor_dotclock = 30M-300M           # dotclock (or pixelclock) range

##
## SDL driver
##

# vo = sdl:aalib        # use SDL video driver by default
                        # use "vo = sdl:aalib" or "vo sdl:dga" and so on,
                        # for specifying SDL subdrivers
# ao = sdl:esd          # use SDL audio driver by default
                        # use "ao = sdl:esd" to use SDL's ESD driver
# noxv = no             # whether to use XVideo hardware acceleration or not
# forcexv = yes         # force XVideo even if not detected

##
## Other (preferred to be default from configfile) switches
##

framedrop=no            # drop frames, when not in sync (slow CPU, videocard,
                        # etc)

#vfm=ffmpeg             # use FFmpeg's libavcodec video codec family
                        # See "mplayer -vfm help" for all available codecs

#bps=yes                # use this method for playing AVIs (if have problems,
                        # try removing this)

# slang= en             # DVD : display english subtitles if available
# alang= en             # DVD : play english audio tracks if available

## This is the correct way to use "subconfig" type options in the
## configuration file. In the command line you use :
## -aop list=resample:fout=44100 , but here it is :
# aop=list=resample:fout=44100

# From Fedora
# the default mpeg audio decoder is currently broken, let's try libmad
# first:
afm=libmad

# get a default OSD font from fontconfig
#fontconfig = yes
#font = "Sans"
#subfont-text-scale = 3



mplayerplug-in.conf
#debug=0
#vo=xv,x11
#ao=arts,esd,oss
#download=1
#dload-dir=$HOME/tmp
#keep-download=0
#noembed=0
#cachesize=512
#use-mimetypes=0
#enable-ogg=1
#enable-smil=1
#enable-helix=1
#qt-speed=med
#rtsp-use-tcp=0
#nomediacache=0
#framedrop=0
#autosync=0
#mc=1
#black-background=0
#user-agent=NSPlayer

---

