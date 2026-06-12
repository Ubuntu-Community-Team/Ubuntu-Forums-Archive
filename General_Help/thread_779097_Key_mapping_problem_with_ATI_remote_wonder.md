---
title: "Key mapping problem with ATI remote wonder"
date: 2008-05-02
forum: General Help
---

### Post by boubbin on 2008-05-02
I am using ATIs Remote Wonder [http://www.mythtv.org/wiki/images/5/5c/Remotewonder1.jpg]("http://www.mythtv.org/wiki/images/5/5c/Remotewonder1.jpg") and i got it working ok with my amarok, but i cant map the FX86AudioNext event to the remote controls Next button.

I recorded the Remote Controllers "next" button 'keycode' with xev and i got:

> FocusOut event, serial 31, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 31, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 31, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967234 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

KeyPress event, serial 31, synthetic YES, window 0x4a00001,
    root 0x188, subw 0x0, time 1, (257,0), root:(1,25404),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic YES, window 0x4a00001,
    root 0x188, subw 0x0, time 1, (257,0), root:(1,25404),
    state 0x4, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (0c) "
                                       "
    XmbLookupString gives 1 bytes: (0c) "
                                         "
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x4a00001,
    root 0x188, subw 0x0, time 1, (257,0), root:(1,25404),
    state 0x4, keycode 46 (keysym 0x6c, l), same_screen YES,
    XLookupString gives 1 bytes: (0c) "
                                       "
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic YES, window 0x4a00001,
    root 0x188, subw 0x0, time 1, (257,0), root:(1,25404),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
and the 'keycode' seems to be 37, but 37 is used by my keyboard as Left control
> KeyRelease event, serial 32, synthetic NO, window 0x4a00001,
    root 0x188, subw 0x0, time 33659559, (516,121), root:(1213,277),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

LeaveNotify event, serial 32, synthetic NO, window 0x4a00001,
    root 0x188, subw 0x0, time 33664210, (518,201), root:(1215,357),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 0
is there any chance to work this around, for example to:
Bind the Remote controllers Next button to some other keycode?
Or use left control with a different key value ?
Thanks

---

