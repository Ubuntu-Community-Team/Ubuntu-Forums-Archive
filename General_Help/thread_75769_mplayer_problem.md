---
title: "mplayer problem"
date: 2005-10-14
forum: General Help
---

### Post by lowey23 on 2005-10-14
I think i have upgraded to breezy. Not sure how to tell if I have or not. Anyway, I cannot get mplayer to work properly. When I try to play a video, I get the following:

Fatal: Could not initialize video filters (-vf) or video output (-vo).

And then I just sit here and wonder what I should do or what it was I did.

Note: had the same thing with hoary.

Could someone help, possibly?

Thanks

---

### Post by pipodnmy on 2005-10-14
run it from the command line (something like mplayer -ao arts -vo xv some.avi) and post the command line that u are running. xv is the most command video output (i think) so you might be using something else.

you can also use some of the graphical frontends to mplayer, like kmplayer or gmplayer which will let you configure this. 

i would in general recommend kaffine (which is a frontend to xine) but i use mplayer when kaffeine craps as well :)

post more details and will try to help u better

---

### Post by lowey23 on 2005-10-14
Thanks very much for your reply. I tried your command and received the following

MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP Thoroughbred (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX



Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing some.
File not found: 'some'
Failed to open some

Playing avi.
File not found: 'avi'
Failed to open avi

Hope this helps.

---

### Post by multios on 2005-10-16
Instead of using "mplayer -ao arts -vo xv some.avi", save your .avi file to hd and then use that name instead of some.avi. 
Example:  mplayer -ao arts -vo xv 100505divx.avi

HTH

---

