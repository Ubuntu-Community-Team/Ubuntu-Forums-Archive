---
title: "games and xfree86-DRI"
date: 2007-11-08
forum: General Help
---

### Post by knowledge_is_power on 2007-11-08
hey, so I have a laptop with an ATI radeon xpress card in there, and im pretty sure that the proprietary drivers (used to accelerate the desktop eyecandy) dont support that extension, causing the message "XFree86-DRI missing on display 1:0"   right, so now i want to play a game... say warsow... and i type "warsow" and i get 
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```
and a little popup box telling me my openGL doesnt support direct rendering and that i should probably install the proprietary driver.
(if i go into the restricted drivers panel, i see that im using ATI accelerated graphics driver, so ???)

now im not sure where to set  LIBGL_DEBUG=verbose but i do know that display :0.0 doesnt give me any flak about XFree86-DRI:
```
d00d@katmandu:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

```

so is there a way to switch to display 0 to play my games?  will that even work?
please help, i just wanna procrastinate...

---

### Post by knowledge_is_power on 2007-11-08
hmmm update, it also seems to be affecting my movie watching...:mad:
for example:
```
d00d@katmandu:~/Downloads$ mplayer The\ Girl\ Next\ Door\ \(2004\)\ \[ENG\]\ \[DVDrip\].avi 
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 (Family: 15, Model: 104, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing The Girl Next Door (2004) [ENG] [DVDrip].avi.
AVI file format detected.
VIDEO:  [XVID]  560x304  12bpp  23.976 fps  741.0 kbps (90.5 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
**Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".**
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Xv: could not grab port 48
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)

```

so after displaying all this, just nothing happens.  it just sits like this and i have to interrupt.
I tried VLC and it manages to play .avi video but no sound and it right freezes the whole GUI.:confused:

please help.

---

### Post by knowledge_is_power on 2007-11-13
anyone?  any suggestions?

---

