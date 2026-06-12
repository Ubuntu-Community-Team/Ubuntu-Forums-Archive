---
title: "Key mapping broken in NX Nomachine after Xubuntu 14.04 upgrade"
date: 2014-05-16
forum: General Help
---

### Post by mikewse on 2014-05-16
After upgrading Xubuntu (x64) 13.10 to 14.04 the Del key is no longer working inside NX Nomachine 3.5.

Opening the NX client desktop locally on the NX server, starting "xev", and pressing Del inside it gives:

```
FocusOut event, serial 36, synthetic NO, window 0x1400001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 36, synthetic NO, window 0x1400001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  82  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
```

while trying "xev" directly on the NX server desktop is working correctly:

```
KeyPress event, serial 37, synthetic NO, window 0x3600001,
    root 0x95, subw 0x0, time 3517687, (91,-14), root:(962,493),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XmbLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyRelease event, serial 37, synthetic NO, window 0x3600001,
    root 0x95, subw 0x0, time 3517783, (91,-14), root:(962,493),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False
```

How can I investigate/solve this?

---

### Post by mikewse on 2014-05-19
While I don't understand exactly why, I got the Delete key working again by removing the keyboard shortcut for PrintScreen.
As I wrote earlier, I'm using the NX client to create a virtual session on the same host as I display it on (nx client, nx server and virtual session are all on the same machine).
Inspecting the keymapping using xmodmap -pke revealed the following on the native X desktop:
```
keycode 107 = Print Sys_Req Print Sys_Req
keycode 119 = Delete NoSymbol Delete
```
and the following on the virtual NX desktop:
```
keycode 107 = Delete
keycode 111 = Print Sys_Req
```
As can be seen there is overlap on keycode 107, and while I think the two sessions SHOULD be able to keep their mappings apart (they did on 13.10) apparently there is still some interference. Note that the PrintScreen key was mapped to a screenshot tool but even though it seems the Delete key inside the NX client had some interference with this mapping it didn't pop this tool.
I guess the root of all this is some corner-case bug in X introduced in Ubuntu 14.04.

---

