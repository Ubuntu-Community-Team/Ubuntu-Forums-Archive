---
title: "Segmentation fault's"
date: 2007-09-05
forum: General Help
---

### Post by argentum2f on 2007-09-05
Occasionally something goes wrong on my system and I start getting seg-faults evertime I try to open certain programs. I thought it was just a firefox problem, but when firefox starts doing it, so do some other programs. Normally they all work just fine. Restarting X fixes the problem temporarily.
Right now I'm using konqueror, which always works fine. Here's what I get from a terminal:
```
jackson@Sensei:~$ firefox
Segmentation fault (core dumped)
jackson@Sensei:~$ firefox
Segmentation fault (core dumped)
jackson@Sensei:~$ vlc
VLC media player 0.8.6 Janus
Segmentation fault (core dumped)
jackson@Sensei:~$ totem
Segmentation fault (core dumped)
jackson@Sensei:~$                      
```

Here's a backtrace of the vlc crash:
```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1213442352 (LWP 12978)]
0xb403d000 in ?? ()
(gdb) bt
#0  0xb403d000 in ?? ()
#1  0xb4dbb961 in gdk_event_apply_filters (xevent=0xbfe77228, event=0x81f6d90,
    filters=0x81cabc0) at gdkevents-x11.c:343
#2  0xb4dbd0cc in gdk_event_translate (display=0x81af100, event=0x81f5d08,
    xevent=0xbfe77228, return_exposes=0) at gdkevents-x11.c:892
#3  0xb4dbecfb in _gdk_events_queue (display=0x81af100) at gdkevents-x11.c:2252
#4  0xb4dbf0ff in gdk_event_dispatch (source=0x81bc130, callback=0,
    user_data=0x0) at gdkevents-x11.c:2312
#5  0xb4b14df2 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#6  0xb4b17dcf in ?? () from /usr/lib/libglib-2.0.so.0
#7  0x0815b388 in ?? ()
#8  0x00000000 in ?? ()
(gdb) 
```

Totem bt:
```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1227401536 (LWP 13025)]
0xb6c39bf3 in ?? ()
(gdb) bt
#0  0xb6c39bf3 in ?? ()
#1  0xb7919961 in gdk_event_apply_filters (xevent=0xbff84ce8, event=0x82efe80,
    filters=0x8193540) at gdkevents-x11.c:343
#2  0xb791b0cc in gdk_event_translate (display=0x81600f0, event=0x81cac20,
    xevent=0xbff84ce8, return_exposes=0) at gdkevents-x11.c:892
#3  0xb791ccfb in _gdk_events_queue (display=0x81600f0) at gdkevents-x11.c:2252
#4  0xb791d0ff in gdk_event_dispatch (source=0x8169450, callback=0,
    user_data=0x0) at gdkevents-x11.c:2312
#5  0xb71aadf2 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#6  0xb71addcf in ?? () from /usr/lib/libglib-2.0.so.0
#7  0x08169498 in ?? ()
#8  0x00000000 in ?? ()
(gdb)             
```

And I attached the output from 'firefox -g'
I hope some of that will be helpful.


Ubuntu 7.04, feisty
Athlon64 3700+
1GB ram
nVidia geforce 6800GT 
1440x900 widescreen for normal display, with a 1024x768 projector also used sometimes (setup as a seperate x server)

Thanks

---

### Post by martinrandau on 2007-09-10
Same problem here...Intel dual core 2 64 bit

---

