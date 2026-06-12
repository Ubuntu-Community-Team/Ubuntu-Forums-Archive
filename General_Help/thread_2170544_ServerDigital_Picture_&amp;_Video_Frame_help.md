---
title: "Server/Digital Picture &amp; Video Frame help"
date: 2013-08-26
forum: General Help
---

### Post by jbenn1680 on 2013-08-26
[CENTER][[IMG]http://img32.imageshack.us/img32/9273/xhyy.jpg[/IMG]](http://imageshack.us/photo/my-images/32/xhyy.jpg/)[/CENTER]

So this is my current work in progress, a digital picture frame from an old laptop running ubuntu server 12.04 LTS.  I've ran into a few issues's that I hope by posting will help me get them resolved so I'm going to post as much info as I can about the system, what I've done so far & how I'm hoping the project will turn out.  I will also try to provide as much detailed info as I can so that anyone else that wants to do something similar will have sort of a guide to by.

Sysinfo -short:
```

H/W path        Device      Class          Description
======================================================
                            system         Latitude C840
/0                          bus            Latitude C840
/0/0                        memory         64KiB BIOS
/0/400                      processor      Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz
/0/400/700                  memory         8KiB L1 cache
/0/400/701                  memory         512KiB L2 cache
/0/1000                     memory         256MiB System Memory
/0/1000/0                   memory         DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
/0/1000/1                   memory         256MiB DIMM DDR Synchronous 266 MHz (3.8 ns)
/0/100                      bridge         82845 845 [Brookdale] Chipset Host Bridge
/0/100/1                    bridge         82845 845 [Brookdale] Chipset AGP Bridge
/0/100/1/0                  display        NV17 [GeForce4 440 Go]
/0/100/1d                   bus            82801CA/CAM USB Controller #1
/0/100/1d.2                 bus            82801CA/CAM USB Controller #3
/0/100/1e                   bridge         82801 Mobile PCI Bridge
/0/100/1e/0     eth0        network        3c905C-TX/TX-M [Tornado]
/0/100/1e/1                 bridge         PCI4451 PC card Cardbus Controller
/0/100/1e/1.1               bridge         PCI4451 PC card Cardbus Controller
/0/100/1e/1.2               bus            PCI4451 IEEE-1394 Controller
/0/100/1f                   bridge         82801CAM ISA Bridge (LPC)
/0/100/1f.1                 storage        82801CAM IDE U100 Controller
/0/100/1f.5                 multimedia     82801CA/CAM AC'97 Audio Controller
/0/100/1f.6                 communication  82801CA/CAM AC'97 Modem Controller
/0/1            scsi0       storage        
/0/1/0.0.0      /dev/sda    disk           40GB IC25N040ATCS04-0
/0/1/0.0.0/1    /dev/sda1   volume         36GiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2   volume         509MiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5   volume         509MiB Linux swap / Solaris partition
/0/1/0.1.0      /dev/cdrom  disk           RW/DVD GCC-4240N
/1              wlan0       network        Wireless interface

```

Sysinfo -Long:
```

frame
    description: Portable Computer
    product: Latitude C840
    vendor: Winbond Electronics
    serial: 
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=

  *-core
       description: Motherboard
       product: Latitude C840
       vendor: Winbond Electronics
       physical id: 0

     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A13
          date: 01/07/2004
          size: 64KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot smartbattery biosbootspecification

     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 Mobile CPU 1.60GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 1200MHz
          capacity: 2500MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts cpufreq
          configuration: id=0

        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data

        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KiB
             capacity: 512KiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified

     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 256MiB
          capacity: 1GiB

        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns) [empty]
             physical id: 0
             slot: DIMM_A
             width: 64 bits
             clock: 266MHz (3.8ns)

        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)

     *-pci
          description: Host bridge
          product: 82845 845 [Brookdale] Chipset Host Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff

        *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:fc000000-fdffffff memory:d8000000-e7ffffff

           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 440 Go]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 vga_controller bus_master vga_palette cap_list rom
                configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
                resources: irq:11 memory:fc000000-fcffffff memory:e0000000-e7ffffff memory:dff80000-dfffffff memory:d8000000-d801ffff

        *-usb:0
             description: USB controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf80(size=32)

        *-usb:1
             description: USB controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:bf20(size=32)

        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 42
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:e000(size=8192) memory:f4000000-fbffffff memory:10000000-17ffffff

           *-network DISABLED
                description: Ethernet interface
                product: 3c905C-TX/TX-M [Tornado]
                vendor: 3Com Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 78
                serial: 
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=32 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:f9000000-f901ffff
           *-pcmcia:0
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f4000000-f4000fff ioport:e000(size=256) ioport:e400(size=256) memory:10000000-13ffffff memory:1c000000-1fffffff

           *-pcmcia:1
                description: CardBus bridge
                product: PCI4451 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1.1
                bus info: pci@0000:02:01.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:11 memory:f8000000-f8000fff ioport:e800(size=256) ioport:f000(size=256) memory:14000000-17ffffff memory:20000000-23ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: PCI4451 IEEE-1394 Controller
                vendor: Texas Instruments
                physical id: 1.2
                bus info: pci@0000:02:01.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:11 memory:f8fff000-f8fff7ff memory:f8ff8000-f8ffbfff

        *-isa
             description: ISA bridge
             product: 82801CAM ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0

        *-ide
             description: IDE interface
             product: 82801CAM IDE U100 Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:11 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:bfa0(size=16) memory:18000000-180003ff

        *-multimedia
             description: Multimedia audio controller
             product: 82801CA/CAM AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:5 ioport:d800(size=256) ioport:dc80(size=64)

        *-communication UNCLAIMED
             description: Modem
             product: 82801CA/CAM AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: generic
             configuration: latency=0
             resources: ioport:d400(size=256) ioport:dc00(size=128)

     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated

        *-disk
             description: ATA Disk
             product: IC25N040ATCS04-0
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CA4O
             serial: CSL405DCCAAWRA
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000612bb

           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 
                size: 36GiB
                capacity: 36GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-08-23 00:02:05 filesystem=ext4 lastmountpoint=/ modified=2013-08-23 00:31:37 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-08-26 06:37:25 state=mounted

           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 509MiB
                capacity: 509MiB
                capabilities: primary extended partitioned partitioned:extended

              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 509MiB
                   capabilities: nofs

        *-cdrom
             description: DVD reader
             product: RW/DVD GCC-4240N
             vendor: HL-DT-ST
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: D110
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.4
       logical name: wlan0
       serial: 
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=3.5.0-39-generic firmware=0.29 ip=192.168.1.109 link=yes multicast=yes wireless=IEEE 802.11abgn


```

For future reference, this is the audio issue that I will refer to later in the post:

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

```

```

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by jbenn1680 on 2013-08-26
So to begin I installed Ubuntu 12.04 LTS server as I wanted to start from bare bones and add only what I needed.  The picture frame is controlled from this pc (windows 7 ultimate) via SSH(Putty), Webmin & Samba for file sharing.

Installed Ubuntu 12.04 LTS
-SSH Server
-Samba
-Installed Webmin later but here's how to do it now:
```
sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl apt-show-versions python
```
```
wget http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb
```
```
sudo dpkg -i webmin_1.580_all.deb
```

With the basics set up and pc booting to prompt:
- sudo apt-get install xorg
- sudo apt-get install xdm
- sudo apt-get install fluxbox
- sudo apt-get install feh

After ensuring that I was able to log into the machine I installed nodm for automatic login
- sudo apt-get install nodm
Edit the nodm config: /etc/default/nodm:
- Change NODM_ENDABLED to TRUE as it is off by default
- Change the NODM_USER to your login/username
```
# nodm configuration

# Set NODM_ENABLED to something different than 'false' to enable nodm
NODM_ENABLED=[COLOR="#FF0000"]true[/COLOR]

# User to autologin for
NODM_USER=[COLOR="#FF0000"]username[/COLOR]

# First vt totruewhen looking for free VTs
NODM_FIRST_VT=7

# X sessiojimDM_XSESSION=/etc/X11/Xsession

# Options for the X server
NODM_X_OPTIONS='-nolisten tcp'

# If an X session will run for less than this time in seconds, nodm will wait an
# increasing bit of time before restarting the session.
NODM_MIN_SESSION_TIME=60
```

reboot to ensure changes have taken effect. 
If everything is working correctly & you have booted/logged in & are looking at fluxbox then we can move on, via either the terminal or SSH(Putty) or webmin edit /home/$USERNAME/.fluxbox/startup:
```
#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "/home/jim/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

[COLOR="#800000"]xset -display :0 -dpms
xset -display :0 dpms 0 0 0
xset -display :0 s 0 0
xset -display :0 s noblank[/COLOR]

[COLOR="#008000"]feh -FZrzD30 /home/jim/Pictures[/COLOR]

#exec fluxbox [COLOR="#FF0000"]--comment out to NOT start fluxbox[/COLOR]

# or if you want to keep a log:
# exec fluxbox -log "/home/[COLOR="#FF0000"]$user[/COLOR]/.fluxbox/log"
```

[COLOR="#800000"]Sets the display to not turn off or blank[/COLOR]
[COLOR="#008000"]Displays images from specified directory i.e.   /home/$user/Pictures
FZrzD30 is the commands for feh
F -  --full-screen
Z - --auto-zoom
r - --recursive
z- --randomize
D - --slideshow-delay NUM i.e. D30 rotates the images in the directory every 30 seconds
[/COLOR]

now edit /home/$user/.bashrc & add the following at the end

```
if [ $(tty) == "/dev/tty1" ]; then
	xset -display :0 -dpms
	xset -display :0 dpms 0 0 0
	xset -display :0 s 0 0
	xset -display :0 s noblank
fi
```

I'm not going to cover much on the samba setup as there are tons of guides on how to do but basically change your WORKGROUP in the config & add a shared folder:
In /etc/samba/smb.conf

WORKGROUP:
```
# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
```
and at the end create the share i.e.
```
[Pictures]
	writeable = yes
	path = /home/jim/Pictures
	force directory mode = 777
	force group = nogroup
	force create mode = 777
	force user = nobody
	comment = 
	public = yes
	create mode = 777
	directory mode = 777
	available = yes
```

and reboot to ensure everything works...

Now since the frame will have no mouse nor keyboard to control it I created a script to restart/refresh feh when I add new images to the Pictures folder

via putty, terminal (if you haven't disassembled the pc yet or webmin create a script called restart.sh (or whatever you want to call it)  in the /home/$user directory i.e. restart.sh & make it executable

-sudo chmod +x *.sh

```
#!/bin/sh
#
# Script to run Digital Picture Frame using Feh
# drware@thewares.net
#

# Change number below to the duration, in seconds
# for each photo to be displayed
DELAY="30"

# Set display so that the script will effect
# the screen on the frame
export DISPLAY=:0

# Stop the currently running Slide show
sudo killall feh

sleep 20s

# Start slide show
feh --quiet --recursive --randomize --full-screen --auto-zoom \
--slide show-delay $DELAY /home/jim/Pictures/ &

exit 0
```

The next post I will talk about my issue's with taking the digital picture frame a bit further and adding video playback to it's ability....which Is what I'm having issues with....

---

### Post by jbenn1680 on 2013-08-26
So I've gotten the frame set up & running the slideshow of my pictures folder (and maybe you have to if you've been following along) but I wanted to take it to the next level and allow the frame to display video's i.e. home & family videos 'n such.  As best as i can recall as I've been working on this for a few days/hours at a time Googling and trying to figure out how to do this I've installed mplayer and can actually run/start a video via ssh.

from a search i edited the mplayer config to contain the following:
```
# Write your default config options here!
fs=yes
zoom=yes
cache=10240
ao=openal
vo=xv
display=:0.0
```

I created a script called random.sh:
```
#!/bin/bash

DIRECTORY=$1

if [ "$1" = "" ]; then
	echo "No directory defined! Using the current directory."
	DIRECTORY="/home/jim/Pictures"
fi

EXTENSION=$2

if [ "$2" = "" ]; then
	echo "No file extension defined! Using avi."
	EXTENSION="mp4"
fi

FILE=$(cd "$DIRECTORY"; find * | grep ${EXTENSION}$ | shuf -n 1) 

PATH="$DIRECTORY/$FILE"

/usr/bin/mplayer -quiet "$PATH"
```

and when i do:
```
jim@Frame:~$ ./random.sh

```

the first (& only .mp4) video i have in the pictures directory will start playing but I get the following output:
```

No directory defined! Using the current directory.
No file extension defined! Using avi.
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/jim/Pictures/Carry on my wayward son supernatural.mp4.
Cache fill:  0.00% (0 bytes)

libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
libavformat file format detected.
[lavf] stream 0: audio (aac), -aid 0, -alang und
[lavf] stream 1: video (h264), -vid 0
VIDEO:  [H264]  480x360  24bpp  30.000 fps  434.2 kbps (53.0 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
 creation_time: 2009-05-16 20:49:50
Load subtitles in /home/jim/Pictures/
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 125.6 kbit/8.90% (ratio: 15696->176400)
Selected audio codec: [ffaac] afm: ffmpeg (FFmpeg AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
xcb_connection_has_error() returned true
xcb_connection_has_error() returned true
AO: [openal] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
Unsupported PixelFormat 53
Unsupported PixelFormat 81
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 480x360 => 480x360 Planar YV12  [fs] [zoom]


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.
```

and after the video is done playing it goes back to displaying images from the FEH slideshow (which is what I want it to do)

what I want the digital picture frame to do is alternate between displaying the images via feh at boot (or restart.sh) and random video's within the directory via mplayer (random.sh).  I don't know how to add more extensions to the EXTENSION variable as i copied the script from someplace else, ideally I would like it to play any kind of format as I have a lot of different kinds .mp4, mkv, avi's, 3gp etc. etc..  That I can play the mp4 is good but the secondary issue is I cannot seem to get the sound working.  The frame if you'll notice in the picture I have a mini bluetooth speaker wired to the frame via line in and can just turn the speaker on and off for sound from video's ....but I can't seem to get the sound working.

I've tried the different audio settings via mplayer ao -help:
the audio output drivers are the following & I've tried some of them but no luck in finding one that works.... 

```
alsa
              ALSA 0.9/1.x audio output driver
                 noblock
                      Sets noblock-mode.
                 device=<device>
                      Sets  the device name.  Replace any ',' with '.' and any
                      ':' with '=' in the ALSA device name.  For hwac3  output
                      via  S/PDIF,  use  an "iec958" or "spdif" device, unless
                      you really know how to set it correctly.

       alsa5
              ALSA 0.5 audio output driver

       oss
              OSS audio output driver
                 <dsp-device>
                      Sets the audio output device (default: /dev/dsp).
                 <mixer-device>
                      Sets the audio mixer device (default: /dev/mixer).
                 <mixer-channel>
                      Sets the audio mixer channel (default: pcm).

       sdl (SDL only)
              highly platform independent SDL (Simple Directmedia  Layer)  li&#8208;
              brary audio output driver
                 <driver>
                      Explicitly  choose the SDL audio driver to use (default:
                      let SDL choose).

       arts
              audio output through the aRts daemon

       esd
              audio output through the ESD daemon
                 <server>
                      Explicitly choose the ESD server to use (default: local&#8208;
                      host).

       jack
              audio output through JACK (Jack Audio Connection Kit)
                 port=<name>
                      Connects  to  the  ports  with  the given name (default:
                      physical ports).
                 name=<client
                      Client name that is passed  to  JACK  (default:  MPlayer
                      [<PID>]).   Useful  if  you want to have certain connec&#8208;
                      tions established automatically.
                 (no)estimate
                      Estimate the audio delay, supposed  to  make  the  video
                      playback smoother (default: enabled).
                 (no)autostart
                      Automatically  start  jackd  if necessary (default: dis&#8208;
                      abled).  Note that this seems unreliable and  will  spam
                      stdout with server messages.

       nas
              audio output through NAS

       coreaudio (Mac OS X only)
              native Mac OS X audio output driver
                 device_id=<id>
                      ID of output device to use (0 = default device)
                 help List all available output devices with their IDs.

       openal
              Experimental OpenAL audio output driver

       pulse
              PulseAudio audio output driver
                 [<host>][:<output sink>]
                      Specify  the host and optionally output sink to use.  An
                      empty <host> string uses a local connection, "localhost"
                      uses network transfer (most likely not what you want).

       sgi (SGI only)
              native SGI audio output driver
                 <output device name>
                      Explicitly  choose  the  output  device/interface to use
                      (default: system-wide default).   For  example,  'Analog
                      Out' or 'Digital Out'.

       sun (Sun only)
              native Sun audio output driver
                 <device>
                      Explicitly  choose  the  audio  device  to use (default:
                      /dev/audio).

       win32 (Windows only)
              native Windows waveout audio output driver

       dsound (Windows only)
              DirectX DirectSound audio output driver
                 device=<devicenum>
                      Sets the device number to use.  Playing a file  with  -v
                      will show a list of available devices.

       kai (OS/2 only)
              OS/2 KAI audio output driver
                 uniaud
                      Force UNIAUD mode.
                 dart Force DART mode.
                 (no)share
                      Open audio in shareable or exclusive mode.
                 bufsize=<size>
                      Set buffer size to <size> in samples (default: 2048).

       dart (OS/2 only)
              OS/2 DART audio output driver
                 (no)share
                      Open DART in shareable or exclusive mode.
                 bufsize=<size>
                      Set buffer size to <size> in samples (default: 2048).

       dxr2 (also see -dxr2) (DXR2 only)
              Creative DXR2 specific output driver

       ivtv (IVTV only)
              IVTV  specific  MPEG  audio output driver.  Works with -ac hwmpa
              only.

       v4l2 (requires Linux 2.6.22+ kernel)
              Audio output driver for V4L2 cards with hardware MPEG decoder.

       mpegpes (DVB only)
              Audio output driver for DVB cards that writes the output  to  an
              MPEG-PES file if no DVB card is installed.
                 card=<1-4>
                      DVB  card  to  use if more than one card is present.  If
                      not specified MPlayer will search the first usable card.
                 file=<filename>
                      output filename

       null
              Produces no audio output but  maintains  video  playback  speed.
              Use -nosound for benchmarking.

       pcm

```

So anyone out there willing to help me firgure this out?

---

### Post by jbenn1680 on 2013-08-26
anyone at all have any input 100+ views & no repsonses....:confused:

---

### Post by jbenn1680 on 2013-08-27
due to lack of response I created a shared Video folder & changed random.sh to the following:
```
#!/bin/bash

DIRECTORY=$1
if [ "$1" = "" ]; then
DIRECTORY="/home/jim/Video"
fi

FILE=$(cd "$DIRECTORY"; find * | grep ${EXTENSION}$ | shuf -n 1) 
PATH="$DIRECTORY/$FILE"

#/usr/bin/totem --fullscreen "$PATH"
/usr/bin/mplayer -quiet "$PATH"
```

which seems to work now.  However that still leaves the no audio issue as well as some sort of script or way to run either restart.sh & random.sh randomly i.e. a script that cycles between the scripts...

---

