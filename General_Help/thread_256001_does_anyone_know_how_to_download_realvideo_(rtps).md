---
title: "does anyone know how to download realvideo (rtps)"
date: 2006-09-12
forum: General Help
---

### Post by matrooswolf on 2006-09-12
Hi, 
does anyone know how to download realvideo (rtps-protocol)?

I try to watch a series of lectures on the internet.
They start up fine in Mplayer (firefox plugin).  
I can watch them as a stream, but I would very much prefer to download it to disk, so I can fastforward to the bits that interest me most.

Its a series of 22 lectures, in total +/- 30 hours.

Any help would be much appreciated!

---

### Post by matrooswolf on 2006-09-18
Hi, nobody any ideas?

---

### Post by droazen on 2006-09-18
Have you tried:

```

mplayer -noframedrop -dumpfile out.rm -dumpstream rtsp://url/to/file.rm

```

That should record the stream to the file out.rm, which you can then view in the player of your choice.

---

### Post by matrooswolf on 2006-09-19
Hi thanks for the reply,
yes I tried something like that, actually this:
```
mplayer -noframedrop -dumpfile out.rm -dumpstream rtsp://140.247.34.92:554/0506s/psy1504/psy1504-060202-v1-hi.rm?gtime=1158003375&guid=b648aff023fa4029863b00B0D04C6A7B&key=A7D504AF5BEE7BD5A62D71E2715CB571&cloakport=80,554,7070/to/file.rm

```
and I got this as error
```


[3]+  Stopped                 mplayer -noframedrop -dumpfile out.rm -dumpstream rtsp://140.247.34.92:554/0506s/psy1504/psy1504-060202-v1-hi.rm?gtime=1158003375
[5]   Done                    key=A7D504AF5BEE7BD5A62D71E2715CB571
matroosje@matroosje:~$ mplayer -noframedrop -dumpfile out.rm -dumpstream rtsp://140.247.34.92:554/0506s/psy1504/psy1504-060202-v1-hi.rm?gtime=1158003375&guid=b648aff023fa4029863b00B0D04C6A7B&key=A7D504AF5BEE7BD5A62D71E2715CB571&cloakport=80,554,7070/to/file.rm
[4] 12580
[5] 12581
[6] 12582
matroosje@matroosje:~$ MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Sempron/Athlon MP/XP/XP-M Barton,Thorton (Family: 6, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Failed to open /dev/rtc: Device or resource busy (it should be readable by the user.)
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

```
I have no idea what it means, can't open joystick?

but maybe I got the url wrong?  Actually, I don't know what part I need to put in.  I tried to cut it different ways, but nothing worked (at least what I tried).

If you have any ideas?

---

### Post by cnhzcy14 on 2006-10-17
thank you so much! this is so helpfull!! is there any way to download mms?

---

### Post by antelao on 2006-12-14
[http://www.ubuntuforums.org/showthread.php?p=2027232#post2027232](http://www.ubuntuforums.org/showthread.php?p=2027232#post2027232)

---

