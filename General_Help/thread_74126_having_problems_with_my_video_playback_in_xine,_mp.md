---
title: "having problems with my video playback in xine, mplayer, and realplay"
date: 2005-10-10
forum: General Help
---

### Post by jpbelauskas on 2005-10-10
here's what i have, an old compaq presario 1200 notebook, with and amd k-6 proc, and an 8 mb matrox video chip.

my problem, 
i try to use mplayer and realplayer, and they lock up. i use the mplayer command in terminal.  in xine, i get a green screen.  i get audio but no video playback.  i used the sudo apt-cache search mplayer-386 to get mplayer and installed with sudo apt-get install mplayer., then did sudo apt-get install mozilla-mplayer.  here's what hapens when i use mplayer

joe@ubuntu:~$ cd ~/Desktop
joe@ubuntu:~/Desktop$ xine mrs_m_stoner.wmv
This is xine (X11 gui) - a free video player v0.99.3.
(c) 2000-2004 The xine Team.
joe@ubuntu:~/Desktop$ mplayer mrs_m_stoner.wmv
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices K6-2 (Family: 5, Stepping: 12)
Detected cache-line size is 32 bytes
CPUflags:  MMX: 1 MMX2: 0 3DNow: 1 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for Debian.


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
Playing mrs_m_stoner.wmv.
ASF file format detected.
VIDEO:  [WMV3]  360x270  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name:
 author:
 copyright:
 comments:
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 32000 Hz, 2 ch, 16 bit (0x10), ratio: 6000->128000 (48.0 kbit)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (ffmpeg))
==========================================================================
vo: X11 running at 800x600 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
GetOutput r=0x0   size:291600  align:1
StreamCount r=0x0  1  1
Decoder supports the following YUV formats: YV12 YUY2 UYVY YVYU   
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 360 x 270 (preferred csp: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 360x270 => 360x270 Planar YV12
Selected video codec: [wmv9dmo] vfm:dmo (Windows Media Video 9 DMO)
==========================================================================
Checking audio filter chain for 32000Hz/2ch/16bit -> 32000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 32000 hz, little endian signed int
AF_pre: 32000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default


MPlayer interrupted by signal 2 in module: enable_cache


MPlayer interrupted by signal 2 in module: ao2_init
joe@ubuntu:~/Desktop$

the video i am trying to play is on my desktop, hence the change in directory.  can anyone help me out with this?

i've used the mplayer -v  movie.wmv, and mplayer -vo x11 movie.wmv commands and nothing works. 

i'm stumped.

i feel i should start over with my players and codecs and everythign but i don't wanna give up yet with out trying everything available.

help? pwetty pwetty pweese?;)

---

### Post by Emerzen on 2005-10-11
I noticed one of your errors was a "permission denied."  Have you tried running Mplayer as root:  

gksudo mplayer

?

---

### Post by jpbelauskas on 2005-10-11
[QUOTE=Emerzen]I noticed one of your errors was a "permission denied."  Have you tried running Mplayer as root:  

gksudo mplayer

?[/QUOTE]


sorry emerz, no suck luck. 

i'm begging to think maybe i should uninstall and reinstall all of the players, codecs and so on and compile from source.  it's just i've never done that before and feel it's a bit over my head at the moment.

any thoughts?

---

### Post by Emerzen on 2005-10-11
Hey, sorry to hear that.  Are you running Hoary or Breezy?

1st - I would update to Breezy if you're running Hoary and can do that.  I have found much fewer problems w/ audio/video in Breezy.

2nd - I would uninstall all of your players and codecs via Synaptic -- and use the "completely uninstall" option so the configuration files are removed as well.  Then go to [www.ubuntuguide.org](www.ubuntuguide.org) and follow the instructions there for installing xine, realplayer, and Mplayer and reinstall.  

3rd - compiling from source - let me know how 1 and 2 go before you try this.

---

### Post by jpbelauskas on 2005-10-11
ive decided to just scrap the whole deal and start from fresh.  so when i reinstalled ubuntu 5.04 from the install disk, i typed server and am now doing everything via CLI.  can you point me to a good guide on installing packages from source?

thanks

joe

---

### Post by Emerzen on 2005-10-11
Here's a quick guide:

1.) install the ubuntu packages:
          build-essential
          checkinstall
          any linux-headers for your kernel version
          often you will need to install the development versions of any dependencies

2.) Download the source software for your architecture (386 vs PPC, etc...)
3.) It's standard to download to /usr/src (create a deb directory in there and a directory for your software) -- this step is not necessary, you can build software from anywhere really, it's mostly just convention and housekeeping

4.) Right click on the package.gz and select "extract here."  You will get a folder w/ the same name minus the .gz extension.  Open this folder and look for a "readme" folder or "install" folder.  Read through this paying particular attention to any special instructions and DEPENDENCIES NEEDED.

5.) Open terminal and change directory (cd) to that folder, whereever it is.  Then, if all is well, do the following:

          **./configure**

          **make**

          **sudo checkinstall**

If all your dependencies are met, this is typically all that is needed.  If you run into errors (pay special attention to errors during configuration) they will often be unmet dependencies.  BTW, checkinstall turns the source into a .deb package that will be accessible via Synaptic after it's finished.

That's the basics...Mplayer is a little more complicated and I have a good thread on it [http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061) .  Sometimes others will list "sudo make install" as the last step...this works but does NOT build a debian package first.  Good luck and have fun...check out this page for practice [http://www.linuxsoft.cz/en/](http://www.linuxsoft.cz/en/)

---

### Post by Emerzen on 2005-10-11
BTW, the version of Mplayer in Hoary was borked the last time I tried it and I followed the thread above to install it from source, which worked flawlessly after that.  Alot of other video software depends on Mplayer working correctly, so I'd start there.  In Breezy, Mplayer was updated and works "out of the box."  Maybe they've updated the Mplayer package in Hoary, maybe not?  It sounds like it may still be the old version w/ bugs.

---

### Post by jpbelauskas on 2005-10-11
emerzen thank you for your replies.  one thing i failed to explain,  i have no gui system, i'm going straight from the command line interface.  could you maybe show me a line on the build-essential, and checkinstall commands?  do you have a good site for starting ubuntu from scratch?

i'm build from the bottom up so to speak. thanks for all of your input thus far.

joe

---

### Post by Emerzen on 2005-10-11
sudo apt-get install build-essential

sudo apt-get install checkinstall

------------------------------------------------------------
Regarding the Mplayer install, if you can read the thread, all the commands are CLI.  Honestly, I've never worked w/out a GUI, at least, available...so good luck.

---

### Post by jpbelauskas on 2005-10-12
hrrrm, got an error on the checkinstall line. couldn't find package checkinstall


any ideas?

---

### Post by Emerzen on 2005-10-12
Do you have all of the repositories added?  Type the following commands and post the list if you can:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

**sudo gedit /etc/apt/sources.list**

You probably don't have the "universe, multiverse, or backports" added.

---

### Post by jpbelauskas on 2005-10-12
[QUOTE=Emerzen]Do you have all of the repositories added?  Type the following commands and post the list if you can:

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup**

**sudo gedit /etc/apt/sources.list**

You probably don't have the "universe, multiverse, or backports" added.[/QUOTE]

i just installed gedit, i'llet you know how it goes from there :)

ok i tried running gedit
sudo gedit /etc/apt/sources.list
password:

(gedit:7858): Gtk-WARNING **: cannot open display:


now heres the thing, i have not installed the ubuntu-desktop yet as i wanted to start everything from scratch and build everything from source. do i need to install the desktop?
can i use gnome with out x windows? if so is the line
apt-get install gnome?

---

### Post by Emerzen on 2005-10-12
No, Gnome needs the X windowing system...I'm 99% sure (there are a couple of windowing systems).  Why are you building the whole thing from source though?  You're a brave person.

---

### Post by jpbelauskas on 2005-10-12
cuz i broke it? hehe, no i decided to reinstall again this time with the ubuntu desktop and learn how to do CLI commands that way first. too brave yet too unfamiliar. 

i'm going straight off of the ubuntu guide to help me out.  if i have any questions i'll give you a buzz :)

---

### Post by Emerzen on 2005-10-12
That's awesome!  I'm not going to keep up w/ this thread then...if you have a question right click on my name and "send a private message."

---

### Post by Wolki on 2005-10-13
[QUOTE=jpbelauskas]i try to use mplayer and realplayer, and they lock up. i use the mplayer command in terminal.  [/QUOTE]

When media players lock upp immediately in Hoary, it's nearly always that the program is not set to use esd. Try to start mplayer with the -ao esd option like this: "mplayer -ao esd <file name>". If it works then, you can set it in your configuration file to automatically use esd, but I forgot exactly how, look at the mplayer documentation. You can also set it from the mplayer GUI.

---

### Post by jpbelauskas on 2005-10-13
thanks i'll try it :)

---

