---
title: "Xbindkeys / Amarok / Ubuntu question"
date: 2008-06-03
forum: General Help
---

### Post by FokkerCharlie on 2008-06-03
Hi

I have a lovely Acer 5920 laptop, which includes, amongst other features, some multimedia keys.  In fact, they work like a touchpad, here's the relevant bit of cat proc/input/devices:

```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio3/input0
S: Sysfs=/devices/platform/i8042/serio3/input/input10
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 0 7001f 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse3 event10 
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003
```

As you can see, there are 2 touchpads there.  One is the regular pad, and the other is the 4 media keys.  With xorg.conf, I have managed to get them working fine- the main touchpad using the synaptics driver, and the media keys using evdev.  Now, the media keys return buttons 17-20 in xev- for instance, pressing the play/pause button:

```
EnterNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2662372, (33,46), root:(1127,102),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2662372, (33,46), root:(1127,102),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

ButtonPress event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x4a00002, time 2662372, (33,46), root:(1127,102),
    state 0x0, button 17, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2662372, (33,46), root:(1127,102),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x4a00002, time 2662416, (33,46), root:(1127,102),
    state 0x0, button 17, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2662416, (33,46), root:(1127,102),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

MotionNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x4a00002, time 2674014, (33,45), root:(1127,101),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x4a00002, time 2674038, (43,39), root:(1137,95),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x4a00002, time 2674054, (63,35), root:(1157,91),
    state 0x0, is_hint 0, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2674078, (83,31), root:(1177,87),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MotionNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2674094, (115,27), root:(1209,83),
    state 0x0, is_hint 0, same_screen YES

MotionNotify event, serial 31, synthetic NO, window 0x4a00001,
    root 0x59, subw 0x0, time 2674118, (139,27), root:(1233,83),
    state 0x0, is_hint 0, same_screen YES
```

Which looks like button 17 has been pressed.  I have mapped this using .xbindkeysrc to alt+ctrl+p:

```
#Play/pause:
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[p]""
  m:0x0 + b:17
```

I then edited the 'Global Shortcuts' in Amarok to use Alt+Ctrl+p as play/pause.  Now, when Amarok is in the background/toolbar, then pressing crt+alt+p plays or pauses.  However, pressing the media key does not!

Here's some xev AFTER xbindkeys has been configured:

```
LeaveNotify event, serial 31, synthetic NO, window 0x4c00001,
    root 0x59, subw 0x4c00002, time 2914996, (41,42), root:(1135,632),
    mode NotifyGrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 0

KeyPress event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x4, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0xc, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (10) ""
    XmbLookupString gives 1 bytes: (10) ""
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0xc, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (10) ""
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0xc, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x4c00001,
    root 0x59, subw 0x0, time 0, (1,1), root:(1,1),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

EnterNotify event, serial 31, synthetic NO, window 0x4c00001,
    root 0x59, subw 0x4c00002, time 2915051, (41,42), root:(1135,632),
    mode NotifyUngrab, detail NotifyVirtual, same_screen YES,
    focus YES, state 0

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  89  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

So, can you tell me how I can complete the puzzle?  I don't see where the problem is- it looks like the media button is mapped correctly.  Amarok is set up with the shortcut.  But somewhere, it's not quite working.

Another quickie while we're here- I'd rather have the buttons mapped to Super+something rather than ctrl+alt+something.  Can anyone give me a clue here?  I can't figure it out.

Thanks in advance!
Charlie

---

### Post by FokkerCharlie on 2008-06-03
Another clue:

The media keys work when Amarok is in the foreground, just not when it's in the background.

So to recap:

Key bindings appear to work, at least from xev and when Amarok is in the foreground.  Global shortcuts for Amarok work, when used direct from the keyboard, but not when using xbindkeys.

Wierd.

---

### Post by FokkerCharlie on 2008-06-05
Solved!

Changed my .xbindkeysrc to:

```
#Mutlimedia Play/pause:
"xvkbd  -text "\[Control_L]\[Alt_L]\[p]""
    m:0x0 + b:17
#Stop: 
"/usr/bin/xvkbd -text "\[Control_L]\[Alt_L]\[s]""
   m:0x0 + b:18
#Multimedia fwd/back:
"/usr/bin/xvkbd -text "\[Control_L]\[Alt_L]\[z]""
    m:0x0 + b:19
"/usr/bin/xvkbd -text "\[Control_L]\[Alt_L]\[x]"" 
    m:0x0 + b:20
```

(Removed -xsendevent from the code entirely).  Now it works perfectly.

Cheerio!
Charlie

---

