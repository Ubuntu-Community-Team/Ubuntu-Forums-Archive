---
title: "Problem with keyboard"
date: 2020-08-02
forum: General Help
---

### Post by rhmerin on 2020-08-02
I am using Ubuntu budgie 20.04.
Today i encountered a problem. 
The 1,q,a,z keys do not working.The keyboard works fine with other device. 
How can i solve this and what is the reason behind this problem???

---

### Post by gdesilva on 2020-08-02
Try running xev command on a terminal and see whether it records the key strokes from 1,q,a,z. You should see something like this...

 KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7675073, (666,594), root:(668,654),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XmbLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7675193, (666,594), root:(668,654),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7675977, (666,594), root:(668,654),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XmbLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7676113, (666,594), root:(668,654),
    state 0x0, keycode 24 (keysym 0x71, q), same_screen YES,
    XLookupString gives 1 bytes: (71) "q"
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7676945, (666,594), root:(668,654),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7677057, (666,594), root:(668,654),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False

KeyPress event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7677881, (666,594), root:(668,654),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XmbLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x5c00001,
    root 0x6b3, subw 0x0, time 7677993, (666,594), root:(668,654),
    state 0x0, keycode 52 (keysym 0x7a, z), same_screen YES,
    XLookupString gives 1 bytes: (7a) "z"
    XFilterEvent returns: False

---

### Post by HermanAB on 2020-08-02
Howdy,

There is a bug in X, where it sometimes forget a key (or four!).  It is not a common problem, but it does happen and I had to fix this a couple times in about 30 years, so welcome to the club - it is quite an exclusive club!

The solution I used, is to check the key code with xev and then explicitly set the key with xmodmap to itself.  This is the same procedure that one would follow if one wants to change the meaning of a key, for example swap the CTRL and CAPSLOCK keys, as many Olde Skool users like to do.

Some googling will get you going.

The other solution, is to re-install the whole system, but that is a bit extreme.

---

