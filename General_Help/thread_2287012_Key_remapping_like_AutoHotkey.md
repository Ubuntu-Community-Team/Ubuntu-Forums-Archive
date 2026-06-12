---
title: "Key remapping like AutoHotkey"
date: 2015-07-16
forum: General Help
---

### Post by lemke_br on 2015-07-16
Hi,

I want to remap some keys to better fit my use. On Windows, I use AutoHotkey and it woks fine. But I cannot do the same on linux. I´ve tried Autokey, but i just won´t do what I want it to do.

My AutoHotkey scitpt is as follows:

```
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
; #Warn  ; Enable warnings to assist with detecting common errors.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

[::`;
RShift & [::Send {:}
LShift & [::Send {:}


`;::/
RShift & `;::Send {?}
LShift & `;::Send {?}

]::'
RShift & ]::Send {"}
LShift & ]::Send {"}

^9::Send {[}
^0::Send {]}


^2::Send {`{}
^3::Send {`}}

'::\
+'::| 
```

Someone knows how can I do the same on Linux?

---

### Post by TheFu on 2015-07-16
This is a question specific to which window manager you are running - probably.  Each WM has a config file - any program/script can be tied to any key-chord you like.  Sadly, I don't have any clue how Unity does this stuff, but openbox has a config file probably in ~/.config/openbox/ ... should be easy to read.  

**xdotool** might be the send-keystrokes-tool you want. I dunno.

Or I could be completely missing the need here. That is highly likely.

---

### Post by lemke_br on 2015-07-17
The need is this: I touch type in Brazilian Portuguese (ABNT2), but my keyboard is US (ANSI, 60%). So I'm adapting the layout. Just rearranging some keys.

For example, I want the ;: key to behave as if it was a /? key.

I installed xdotool from the repositories, but I'm lost.

I tried **xdotool key semicolon slash** thinking it would change the behavior of ; key. But actually, it sends ;/ to the terminal. Not very useful.

---

### Post by TheFu on 2015-07-17
Here's an example from my openbox conf file inside the  <keyboard> section:
```
    <keybind key="C-BackSpace">
        <action name="Execute">
              <command>/usr/bin/xdotool key --clearmodifiers Delete</command>
         </action>
    </keybind>
```
My chromebook doesn't have a delete key, so I map CNTL-Backspace to be Delete. Make sense?

On my box, the openbox conf is ~/.config/openbox/rc.xml --- just check the process arguments for the RC file used.  Of course, you may not be using openbox as a WM. Then you'll need to figure out which WM is running, find the config file for it, figure out the way to map keys to programs, .... if you are running Unity, I cannot help at all and suspect all of this is worthless.

---

### Post by lemke_br on 2015-07-18
Ah! It makes way more sense.

I'm using MATE. Now I'm trying to find the file that does the same thing in this WM.

---

### Post by TheFu on 2015-07-18
Mate is a DE, not a WM.
[https://www.maketecheasier.com/replace-mate-window-manager-with-openbox/](https://www.maketecheasier.com/replace-mate-window-manager-with-openbox/) might make this easier.

---

