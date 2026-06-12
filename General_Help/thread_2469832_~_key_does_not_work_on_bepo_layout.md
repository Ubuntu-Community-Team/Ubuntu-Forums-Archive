---
title: "~ key does not work on bepo layout"
date: 2021-12-11
forum: General Help
---

### Post by gilles9 on 2021-12-11
Hello everybody,
I wanted to write some php on my ubuntu desktop 20.04 distribution and I realized that the tilde key below the key esc does not work. ~ So I can't type the dollars key. I have tried on a different ubuntu 20.04 distribution on a another hard drive but I have still the same problem. 
Does anyone have a suggestion or is it a know bug ? 
Thank you in advance.
*edit
Even with other keyboard layouts the tilde key doesn't work

---

### Post by Impavidus on 2021-12-11
I assume you're using this layout: [https://en.wikipedia.org/wiki/B%C3%89PO](https://en.wikipedia.org/wiki/B%C3%89PO)
That appears to be a pretty exotic layout, making bugs more likely, but if offered by Ubuntu, I would expect it to work.

What do you get using the xev tool? Run xev from command line, then (with the little xev window in focus), hit the key. On my US qwerty keyboard, I get```

# Press tilde key
KeyPress event, serial 34, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6771968, (-188,-176), root:(406,129),
    state 0x10, keycode 49 (keysym 0x60, grave), same_screen YES,
    XLookupString gives 1 bytes: (60) "`"
    XmbLookupString gives 1 bytes: (60) "`"
    XFilterEvent returns: False

# Release tilde key
KeyRelease event, serial 37, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6772009, (-188,-176), root:(406,129),
    state 0x10, keycode 49 (keysym 0x60, grave), same_screen YES,
    XLookupString gives 1 bytes: (60) "`"
    XFilterEvent returns: False

# Press shift key
KeyPress event, serial 37, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6776662, (-188,-176), root:(406,129),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

# Press tilde key
KeyPress event, serial 37, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6777393, (-188,-176), root:(406,129),
    state 0x11, keycode 49 (keysym 0x7e, asciitilde), same_screen YES,
    XLookupString gives 1 bytes: (7e) "~"
    XmbLookupString gives 1 bytes: (7e) "~"
    XFilterEvent returns: False

# Release tilde key
KeyRelease event, serial 37, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6777474, (-188,-176), root:(406,129),
    state 0x11, keycode 49 (keysym 0x7e, asciitilde), same_screen YES,
    XLookupString gives 1 bytes: (7e) "~"
    XFilterEvent returns: False

# Release shift key
KeyRelease event, serial 37, synthetic NO, window 0x4c00001,
    root 0x13e, subw 0x0, time 6778577, (-188,-176), root:(406,129),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```xev is supposed to show the keypress even if no character is assigned to the key, so if xev doesn't show it, the keypress is never reported to the application, i.e., intercepted before or the keyboard is broken.

---

### Post by gilles9 on 2021-12-12
I'm sure my keyboard is broken since I tried with windows and with an external keyboard.
Thank you for your help and sorry for having posted so quickly. 
have a nice day.

---

