---
title: "MPlayer crash when attempting to dumpstream YouTube video"
date: 2007-06-27
forum: General Help
---

### Post by srunni on 2007-06-27
Hi,

I was trying to using MPlayer's dumpstream feature to dump a YouTube video of a Ron Paul (great guy!) CNN debate to my HDD. However, when I attempted to do so, I got the following error: ```
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 3.00GHz (Family: 15, Model: 4, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://www.youtube.com/v/pwJKGfAWQUo.
Resolving www.youtube.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.youtube.com
Resolving www.youtube.com for AF_INET...
Connecting to server www.youtube.com[208.65.153.253]: 80...
Resolving www.youtube.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.youtube.com
Resolving www.youtube.com for AF_INET...
Connecting to server www.youtube.com[208.65.153.251]: 80...


MPlayer interrupted by signal 11 in module: open_stream
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

Could anybody help me out with this? I'd really like to be able to dump the videos to my HDD this way, instead of having to use the VideoDownloader Firefox plugin.

Thanks in advance for the help!!

---

### Post by eggdeng on 2007-06-28
Tried this and got the following error

```
Playing http://www.youtube.com/watch?v=8Hfa7vT02lA[.
Resolving www.youtube.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.youtube.com
Resolving www.youtube.com for AF_INET...
Connecting to server www.youtube.com [208.65.153.251]: 80...
Cache size set to 320 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
```

I find Video Downloader to work pretty well.

---

### Post by mcduck on 2007-06-28
I always just copy the video from /temp to my desktop and then use ffmpeg2theora to convert it into .ogg video..

---

### Post by eggdeng on 2007-06-28
The folder on my system (Dapper) is called /tmp but OK, that works really well. Thanks.

---

### Post by srunni on 2007-06-28
> **mcduck said:**
> I always just copy the video from /temp to my desktop and then use ffmpeg2theora to convert it into .ogg video..

I'll try that - what's the command you use to convert to .ogg? EDIT: I got it, just do ```
ffmpeg2theora foo.flv
```

> **eggdeng said:**
> Tried this and got the following error

```
Playing http://www.youtube.com/watch?v=8Hfa7vT02lA[.
Resolving www.youtube.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.youtube.com
Resolving www.youtube.com for AF_INET...
Connecting to server www.youtube.com [208.65.153.251]: 80...
Cache size set to 320 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
```

I find Video Downloader to work pretty well.

I've actually found it to be quite temperamental, so I think I'll just try copying the file from /tmp .

---

