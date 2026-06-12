---
title: "Using DOSbox for first time"
date: 2006-08-29
forum: General Help
---

### Post by RaoulDuke on 2006-08-29
While cleaning out our computer room last weekend, I found a bunch of our old 3.5 floppies, and even some REAL 5.25 FLOPPIES (including our first copy of Windows 3.0). I found several old DOS games in the 3.5 floppies, so I thought I would check out a DOS emulator and see if I could get some of these old games running.

Just installed DOSbox from source, everything went fine and it runs. I figured I would try to install Hero's Quest II to start off.

Install runs fine until it asks for Disk 2. It says Press Any Key to Continue, and keeps repeating that every time I Press Any Key (and yes I did put Disk 2 in).

Any suggestions?

---

### Post by simonn on 2006-08-29
What I suspect is happening is that dosbox is not recognising the disk change so the installer just sees the same files - even though they are not there.

Try copying all the files of both floppies to one directory on the harddrive. Then, in dosbox, mount that dir as A: and try to install.

Worst comes to worse, download freedos, boot into it and install the game. Copy the installed files to a directory somewhere and run them from dosbox. zip/tar up the installed files to keep for the future.

---

### Post by RaoulDuke on 2006-08-30
I don't know why I didn't think of that, thanks!

It never bothers to ask for another disk and it looks as if it installs fine, but then when I try to run it it says it's unable to install the video drivers.

Thanks again

---

### Post by RaoulDuke on 2006-08-30
sorry, just testing my profile picture, doesn't seem to want to work for me yet

---

### Post by mucho_maze on 2006-09-09
Hey there, I can't find out how to enter the dosbox config file, where I can configure the language I want to use for the keyboard. I can't type ":" so therefor I can't load any of my mounted drives... Any suggestions??

---

### Post by graigsmith on 2006-09-25
one thing you can do, dosbox recognises the system's keyboard layout, so if you change it to english standard, it should give your keyboard the ability to use that.
 
but you can also use the config file to mount, and load the program.

example.
start dosbox like this, you can specify a conf file.
```
dosbox -conf /home/graig/Games/DOS/default.conf
```

ok, and this is the insides of the config file. at the bottom is an autoexec section, and you can actually just type the commands in there. 
cd lol changed to my games directory, and lands ran the program.

you can make seperate config files for each game you have.  and then start them with an icon that specifies the correct config file.

```
[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullfixed -- Don't resize the screen when in fullscreen.
# fullresolution -- What resolution to use for fullscreen, use together with fullfixed.
# output -- What to use for output: surface,overlay,opengl,openglnb.
# hwscale -- Extra scaling of window if the output device supports hardware scaling.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lower,normal,higher,highest.
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.

fullscreen=false
fulldouble=false
fullfixed=false
fullresolution=1024x768
output=overlay
hwscale=1.90
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=/home/graig/DOS/lol.txt

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory dosbox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
captures=capture
memsize=16

[render]
# frameskip -- How many frames dosbox skips before drawing one.
# aspect -- Do aspect correction.
# scaler -- Scaler used to enlarge/enhance low resolution modes.
#           Supported are none,normal2x,advmame2x,advmame3x,advinterp2x,interp2x,tv2x.

frameskip=0
aspect=false
scaler=normal2x

[cpu]
# core -- CPU Core used in emulation: simple,normal,full,dynamic.
# cycles -- Amount of instructions dosbox tries to emulate each millisecond.
#           Setting this higher than your machine can handle is bad!
# cycleup   -- Amount of cycles to increase/decrease with keycombo.
# cycledown    Setting it lower than 100 will be a percentage.

core=normal
cycles=15000
cycleup=500
cycledown=500

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
# mpu401      -- Enable MPU-401 Emulation.
# intelligent -- Operate in Intelligent mode.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device.

mpu401=true
intelligent=true
device=default
config=

[sblaster]
# type -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# base,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the dosbox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
# oplrate -- Sample rate of OPL music emulation.

type=sb16
base=220
irq=7
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

[gus]
# gus -- Enable the Gravis Ultrasound emulation.
# base,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# rate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=true
rate=22050
base=240
irq1=5
irq2=5
dma1=3
dma2=3
ultradir=C:\ULTRASND

[speaker]
# pcspeaker -- Enable PC-Speaker emulation.
# pcrate -- Sample rate of the PC-Speaker sound generation.
# tandyrate -- Sample rate of the Tandy 3-Voice generation.
#              Tandysound emulation is present if machine is set to tandy.
# disney -- Enable Disney Sound Source emulation.

pcspeaker=true
pcrate=22050
tandyrate=22050
disney=true

[bios]
# Nothing to setup yet!


[dos]
# xms -- Enable XMS support.
# ems -- Enable EMS support.

xms=true
ems=true

[modem]
# modem -- Enable virtual modem emulation.
# comport -- COM Port modem is connected to.
# listenport -- TCP Port the modem listens on for incoming connections.

modem=false
comport=2
listenport=23

[ipx]
# ipx -- Enable ipx over UDP/IP emulation.

ipx=false

[autoexec]
# Lines in this section will be run at startup.
mount c /home/graig/DOS
c:
cd lol 
lands

```

---

