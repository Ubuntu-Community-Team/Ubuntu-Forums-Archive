---
title: "Problem with one key on the keyboard."
date: 2006-11-02
forum: General Help
---

### Post by Anbern on 2006-11-02
I can use  every button on my keyboard except the most important one for me, the &lt; and &gt;-key, as I mostly use the computer for web developing this is quite a problem as you might understand.

If anyone has any idea about why this is happening or has a solution it would be greatly appreciated.

Oh, and I forgot to add: I'm using Kubuntu.

---

### Post by adwait on 2006-11-02
Nevermind.........stupid me

---

### Post by Anbern on 2006-11-02
This might help? I get the following from pressing the key i want to use:

> 
KeyPress event, serial 31, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 2828730283, (-487,856), root:(108,880),
    state 0x0, keycode 94 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 2828730443, (-487,856), root:(108,880),
    state 0x0, keycode 94 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False


And the following from pressing 'p':
> 
KeyPress event, serial 31, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 2828785022, (-524,862), root:(71,886),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3600001,
    root 0x4d, subw 0x0, time 2828785190, (-524,862), root:(71,886),
    state 0x0, keycode 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False


---

### Post by aschlapsi on 2006-11-04
> **Anbern said:**
> I can use  every button on my keyboard except the most important one for me, the &lt; and &gt;-key, as I mostly use the computer for web developing this is quite a problem as you might understand.

If anyone has any idea about why this is happening or has a solution it would be greatly appreciated.

Oh, and I forgot to add: I'm using Kubuntu.

I had the same problem. I solved it by starting the KDE Control Center (kcontrol) and setting the keyboard type to Generic 105-key. You can find this setting at Regional Settings -> Keyboard Layout.

---

