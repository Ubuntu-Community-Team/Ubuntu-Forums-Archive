---
title: "cd playback choppy, everything slow"
date: 2005-09-30
forum: General Help
---

### Post by leonardmead on 2005-09-30
when I play cd's the sound is choppy (i.e. plays for a second, stops, plays for a second, stops ...).  Also, everything (opening windows, menus, programs) is generally slow. Is it that my processor just can't handle Unbuntu? This is a laptop from 2000.

If this is a processor problem, is there any way that I can dumb down/simplify the OS a bit so there isn't so much going on in the background?

---

### Post by mlomker on 2005-09-30
You could try opening a terminal and running **top** to see what it is.  It could be that you're low on memory...is the hard disk light on all of the time?  Accessing the hard disk really slows down laptops.

---

### Post by leonardmead on 2005-09-30
It's not accessing the hard drive all the time.  (also: what does that "2 users" at the begging mean?)

Here are two printouts from TOP:

Without cd playing

top - 08:59:02 up  4:55,  2 users,  load average: 0.47, 0.25, 0.12

Tasks:  69 total,   1 running,  68 sleeping,   0 stopped,   0 zombie

Cpu(s): 10.4% us,  1.5% sy,  0.0% ni, 84.4% id,  3.4% wa,  0.3% hi,  0.0% si

Mem:     62044k total,    60328k used,     1716k free,     1316k buffers

Swap:   176672k total,    66412k used,   110260k free,    16236k cached
------------------------
With cd playing

top - 10:00:54 up  5:57,  2 users,  load average: 2.54, 1.12, 0.60

Tasks:  72 total,   1 running,  71 sleeping,   0 stopped,   0 zombie

Cpu(s): 26.6% us,  4.5% sy,  0.0% ni, 57.4% id,  7.4% wa,  4.2% hi,  0.0% si

Mem:     62044k total,    60404k used,     1640k free,      568k buffers

Swap:   176672k total,    77004k used,    99668k free,    17008k cached

---

### Post by mlomker on 2005-09-30
64 MB of RAM?  Yikes.  You have more swapped out than physical RAM.  Oh, well...if you say it isn't thrashing the drive.

You've checked out the DMA settings on your drive (hdparm)?  I probably wouldn't run gnome on a box with that amount of memory.  Maybe explore XFCE/iceWM/or even TWM as a window manager?  They aren't as pretty but they run programs and use less memory.

---

### Post by leonardmead on 2005-09-30
Yeah, basically the situation is that this thing isn't worth spending any money on, I just have dial-up, so downloading an OS is out of the question, and some guy handed me an Unbuntu disk, so I thought I'd try it out.

Thanks for your help!

---

### Post by bluntz on 2007-10-02
Im having choppy playback on audio/video/cd/dvd on a p3 300+ megs ram also ,so its not just a
machine issue..
TONS of folks are having the same problem with edgy,some kind of buffering bug.I think
just do a google for choppy ubuntu and youll see what I mean...lol
I got a tpad with 16 megs ram 166 pentium that runs xmms streamtuner with no chop at all.
so I have a hard time buying the crappy hardware excuse on a linux system!

---

