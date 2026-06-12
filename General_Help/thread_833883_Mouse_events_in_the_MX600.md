---
title: "Mouse events in the MX600"
date: 2008-06-19
forum: General Help
---

### Post by dmsuperman on 2008-06-19
So I've tried googling and haven't really found any results.

I'd love to use btnx for my problem, if that's at all possible.


I have a Logitech MX600 USB mouse, which uses a wireless USB reciever.


Basically, when using xev to detect my extra mouse buttons, I don't get any good results. My results:



Left click:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671025058, (110,0), root:(120,98),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671025544, (110,0), root:(120,98),
    state 0x110, button 1, same_screen YES
```


Right click:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671105744, (162,-1), root:(172,97),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671105853, (162,-1), root:(172,97),
    state 0x410, button 3, same_screen YES
```


Middle click:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671163328, (59,0), root:(69,98),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671164056, (59,0), root:(69,98),
    state 0x210, button 2, same_screen YES
```

Zoom 100%:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671196754, (79,1), root:(89,99),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671199266, (79,1), root:(89,99),
    state 0x210, button 2, same_screen YES
```


Thumb left:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671268178, (60,3), root:(70,101),
    state 0x10, button 3, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671268262, (60,3), root:(70,101),
    state 0x410, button 3, same_screen YES
```


Thumb right:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671334162, (103,-2), root:(113,96),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671334770, (103,-2), root:(113,96),
    state 0x210, button 2, same_screen YES
```


Tilt left:

```
ButtonPress event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671528845, (98,6), root:(108,104),
    state 0x10, button 2, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9000001,
    root 0x1a5, subw 0x0, time 2671530997, (98,6), root:(108,104),
    state 0x210, button 2, same_screen YES
```


Scroll down:

```
ButtonPress event, serial 31, synthetic NO, window 0x9400001,
    root 0x1a5, subw 0x0, time 2672586538, (164,99), root:(174,197),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9400001,
    root 0x1a5, subw 0x0, time 2672586538, (164,99), root:(174,197),
    state 0x1010, button 5, same_screen YES
```


Scroll up:

```
ButtonPress event, serial 31, synthetic NO, window 0x9400001,
    root 0x1a5, subw 0x0, time 2672639325, (127,139), root:(137,237),
    state 0x10, button 4, same_screen YES

ButtonRelease event, serial 31, synthetic NO, window 0x9400001,
    root 0x1a5, subw 0x0, time 2672639325, (127,139), root:(137,237),
    state 0x810, button 4, same_screen YES
```


Tilt right, Zoom+ and Zoom- all don't even give an event.


I'd like to map tilt left and tilt right to change workspaces (previous and next respectively), zoom in to next track, zoom out to previous track, and zoom 100% to pause/play. The thumb left/right buttons I'd like to map to forward/back (if I must choose, I'd like them to be forward/back in firefox).


btnx detects all my buttons, however when I actually press a button it never executes the keypress that I tell it to.


Can anybody help me figure out how to set my mouse buttons properly to what I want them as?

---

### Post by dmsuperman on 2008-06-22
Nobody knows anything about this?

---

### Post by jonlemur on 2008-07-10
It may be too late, but I think you can use xbindkeys to map stuff like that.  This [thread]("http://ubuntuforums.org/showthread.php?t=219894") probably has a lot of the information you need.  I'll read through your post more carefully tomorrow to see if I can help, but that would be a good place to start.

---

