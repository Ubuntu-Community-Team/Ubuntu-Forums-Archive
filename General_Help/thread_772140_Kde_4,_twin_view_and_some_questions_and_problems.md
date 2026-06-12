---
title: "Kde 4, twin view and some questions and problems"
date: 2008-04-28
forum: General Help
---

### Post by eXt on 2008-04-28
Hi all!

I've got a fresh instal of Hardy Heron Remix (KDE 4). It has installed smoothly and is quite stable, but there is some annoying things.

I have nvida geforce 8600 and dual head configuration. 

1. Xinerama. Up till now (Gutsy) I used Xinerama. Now on 8.04 enabling Xinerama causes Desktop Effects to be unavailable (It complains about xcomposite and xdamage being not available). Except that it works nicely with one exception - maximized windows are rendered below the panel so I don't see for example status bars etc. I was not able to change this behavior :/ Hints?


2. I have used Twin View instead of Xinerama. It works similiarly to Xinerama but:

2.1 I wonder what will happen when I plug another monitor to my laptop.. will it be autodetected like it was with xinerama? 

2.2. Is it possible to move "The panel" (the one with running programs etc.) from one screen to another? It is currently displayed on my laptop's screen and I'd like it to be shown on external monitor.

2.3 I have OpenGL composition enabled but I can't enable XRender one because it raises an critical exception. Traceback:
"
0xb7f06410 in __kernel_vsyscall ()
[Current thread is 0 (process 25438)]

Thread 1 (Thread 0xb5d23740 (LWP 25438)):
#0  0xb7f06410 in __kernel_vsyscall ()
#1  0xb7d92c90 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d92ac7 in sleep () from /lib/tls/i686/cmov/libc.so.6
#3  0xb70937d0 in ?? () from /usr/lib/kde4/lib/libkdeui.so.5
#4  0x00000001 in ?? ()
#5  0x00000000 in ?? ()
#0  0xb7f06410 in __kernel_vsyscall ()
"
By the way - which composition should I prefer? OpenGL or XRender? What is the difference?

2.4 I often see random geometrical figures on my screen.. like something is not refreshed properly.

3. I've read somewhere that contents of Desktop folder should be shown on the Desktop. Is that true? It doesnt't work for me :(

regards
eXt

---

