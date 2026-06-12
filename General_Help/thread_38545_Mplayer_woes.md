---
title: "Mplayer woes"
date: 2005-05-31
forum: General Help
---

### Post by elasticwings on 2005-05-31
Okay, I've spent some time wondering around and reading all the how-tos and postings on Mplayer problems.  I've installed via apt with the multiverse repos and grabbed w32codecs from the Marillet repos.  I am trying my hardest to get mplayer to play divx encoded avi files and ogm files from a windows networked computer serving the files.  I have the windows share mounted via fstab with smbfs support installed.  Every time I try to play a divx encoded avi file mplayer locks.  I have to kill it's process after that.  Clicking on the close X at top won't work.  OGM, I will have to go back and look to see how it reacts.  Any help would be appreciated.

---

### Post by Xerampelinae on 2005-05-31
so... does mplayer work on local files?

---

### Post by elasticwings on 2005-06-01
Not sure, I will try copying the files to the local drive and playing them when I get home tonight.

---

### Post by elasticwings on 2005-06-01
Okay, just tried the same thing on the work computer with a local avi file that is divx encoded.  It still locks up, and I have to kill its process.

---

### Post by elasticwings on 2005-06-01
Here is what I get in the console when I launch it and try to open a divx/xvid file.

```
wperkins@sailormoon:~$ gmplayer
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Opteron Sledgehammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE




vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
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
Playing /home/wperkins/WonderShowzen/Wonder.Showzen.-.106.-.History.xvid.avi.
AVI file format detected.
VIDEO:  [XVID]  512x384  12bpp  29.970 fps  1021.2 kbps (124.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 16000->192000 (128.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
```

---

### Post by Xerampelinae on 2005-06-01
sudo echo 1024 > /proc/sys/dev/rtc/max-user-freq

?

---

### Post by Hydrant on 2005-06-01
Try running it with the 'mplayer' command line instead of Gmplayer. This will answer whether its the video itself, or the GUI. I've often had troubles with its gui version myself, so I stick exclusively to CLI mplayer.
Try it and let us know.

---

### Post by elasticwings on 2005-06-02
I'm working on trying the echo command line that it issues.  I ran it on my work machine earlier today, but I was running a script on another machine that I had to keep an eye on then I got busy during the end of the day.  Then, I went to a karaoke bar and got home too late to try it at home.  I will post tomorrow how the results go.  Thanks!

---

### Post by elasticwings on 2005-06-02
Okay, I did the echo 1024 > /proc/sys/dev/rtc/max-user-freq thing in a startup script.  I'm still locking up though.  Here is an updated paste of what output I get.

```
wperkins@sailormoon:~$ gmplayer
MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Opteron Sledgehammer (Family: 8, Stepping: 10)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE




vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/wperkins/family.guy.403.pdtv-lol.avi.
Cache fill:  0.00% (0 bytes)    AVI file format detected.
VIDEO:  [XVID]  512x384  12bpp  23.976 fps  987.5 kbps (120.5 kbyte/s)
Clip info:
 Software: VirtualDub
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, 16 bit (0x10), ratio: 16000->192000 (128.0 kbit)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/16bit -> 48000Hz/2ch/16bit...
AF_pre: af format: 2 bps, 2 ch, 48000 hz, little endian signed int
AF_pre: 48000Hz 2ch Signed 16-bit (Little-Endian)
alsa-init: got device=0, subdevice=0
alsa-init: 1 soundcard found, using: default
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 149
[ws]  Minor code: 1
[ws]  Modules: enable_cache
[ws] Error in display.
[ws]  Error code: 14 ( BadIDChoice (invalid resource ID chosen for this connection) )
[ws]  Request code: 1
[ws]  Minor code: 0
[ws]  Modules: ao2_init
```

---

### Post by elasticwings on 2005-06-02
Ugh, nevermind.  I found it.  I can't freaking believe this.  I changed from Alsa to ESD and now it works.  Thanks all for the help.  I feel so stupid now.   ](*,)

---

### Post by elasticwings on 2005-06-03
Okay, so I have Mplayer playing some files, but when I select full screen.  The video size doesn't change, it just puts black around the rest of the screen.  I can't play the ogm file still, and I can only play some divx files whereas others I can't.

---

### Post by Xerampelinae on 2005-06-03
Try running mplayer with the "-vo xv" option, or try setting it perminantly in /etc/mplayer.conf

---

### Post by elasticwings on 2005-06-04
I tried that.  I'm assuming that was to help with the fullscreen issue.  It didn't change anything though.  :(

---

### Post by elasticwings on 2005-06-04
Nevermind, you were right.  I had to do it in the gui.conf file located in .mplayer under my profile also.  Thanks.

Any ideas on the files I can't play?

---

### Post by Xerampelinae on 2005-06-04
sorry, I don't have any ideas about the ogm and divx file issue.

A bad solution is to perhaps try using xine-ui if you just want to view the files..

---

### Post by elasticwings on 2005-06-04
I figured that one out finally.  For some unknown reason, Windows XP decided that even though I shared a top level folder, it wouldn't pass the permissions to the next level folder.  I figured it out when I tried to cp it to my home folder to try and run it there.  I had to create a new folder then move the file into that folder and rename the folder.  Stupid Windows!!!  That's the reason my living room computer isn't a WinBrick.

---

