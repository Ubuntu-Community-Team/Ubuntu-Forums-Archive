---
title: "after upgrade launcher apps do not load"
date: 2006-11-04
forum: General Help
---

### Post by gu014 on 2006-11-04
hello, i am having a problem with my bottom launcher panel.  i.e. one of the launchers has "wine /home/sean/.wine/drive_c/Program\ Files/DVD\ Shrink/DVD\ Shrink\ 3.2.exe" for its command....when i click on the icon nothing happens...however, when i run the same command from the console it loads with the following messages:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme: ole:CoRegisterMessageFilter message filter has been registered, but will not be used
err: x11drv:X11DRV_CreateWindow invalid window height -21
err: x11drv:X11DRV_CreateWindow invalid window height -21
err: listview:LISTVIEW_WindowProc unknown msg 1044 wp=00000000 lp=0033dc10
fixme:  devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme: devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found



..would anyone be able to help me out?>

---

### Post by ingo on 2006-11-05
i didn't get whether dvd shrink actually comes up or not, but there is a native dvd backup programme which as yet does not give a toss about the latest protection codes (well, not those I have tried), namely k9copy. it works a treat :)

---

### Post by gu014 on 2006-11-05
> **ingo said:**
> i didn't get whether dvd shrink actually comes up or not, but there is a native dvd backup programme which as yet does not give a toss about the latest protection codes (well, not those I have tried), namely k9copy. it works a treat :)

yes, i have used the program, but IMO the program is rather bloated and unfortunately i prefer dvd shrink.  

and the app does not load from the launcher panel......

---

### Post by ingo on 2006-11-06
can you make it start at all? if not, have you tried reinstalling?  how is wine behaving with other windows programmes?

---

