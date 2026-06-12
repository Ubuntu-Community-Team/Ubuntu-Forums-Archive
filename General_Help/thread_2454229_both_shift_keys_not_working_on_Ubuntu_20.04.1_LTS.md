---
title: "both shift keys not working on Ubuntu 20.04.1 LTS"
date: 2020-11-25
forum: General Help
---

### Post by diegooc on 2020-11-25
im using a laptop and my shift keys aren't working, on the same  laptop i've also windows and when i use it both shifts work normally, so  it's not a mechanical problem.


 can you please help me diagnose and fix this issue 'question mark'


 thanks
     

xev result

KeyPress event, serial 37, synthetic NO, window 0x1e00001,
    root 0x224, subw 0x0, time 11213734, (61,-16), root:(62,49),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x1e00001,
    root 0x224, subw 0x0, time 11213750, (61,-16), root:(62,49),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

i think that the system is interpreting 'at  random' that when i press shift and the system identifies it, it  comprehend as it was being pressed and released instead just pressed.  please need some help fixing this issue, it's impossible to use the  keyboard properly with this issue

---

