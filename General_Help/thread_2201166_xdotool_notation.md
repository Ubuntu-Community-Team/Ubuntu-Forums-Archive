---
title: "xdotool: notation?"
date: 2014-01-22
forum: General Help
---

### Post by vasa1 on 2014-01-22
From examples on the net or by reading the xdotool man page (or from trial an error) I can pick up a few things like I should use "space" and not "Space" or "Super_L" and not "super" "Windows" as keys.

Where can I find the full list?

---

### Post by stinkeye on 2014-01-22
```
sudo apt-get install x11proto-core-dev
```

Find the main keys ... 
```
gedit /usr/include/X11/keysymdef.h
```

and distro specific keys in...
```
gedit /usr/include/X11/XF86keysym.h
```


I have also opened a terminal and ran
 ```
xev &
```
Press left control key and you should see output similar to....

```
KeyPress event, serial 40, synthetic NO, window 0x6600001,
    root 0x295, subw 0x0, time 4648074, (-293,159), root:(482,607),
    state 0x10, keycode 37 (keysym 0xffe3, [COLOR="#FF0000"]Control_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x6600001,
    root 0x295, subw 0x0, time 4648162, (-293,159), root:(482,607),
    state 0x14, keycode 37 (keysym 0xffe3, [COLOR="#FF0000"]Control_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

---

### Post by vasa1 on 2014-01-23
> **stinkeye said:**
> ...
I have also opened a terminal and ran
 ```
xev &
```
Press left control key and you should see output similar to....

```
KeyPress event, serial 40, synthetic NO, window 0x6600001,
    root 0x295, subw 0x0, time 4648074, (-293,159), root:(482,607),
    state 0x10, keycode 37 (keysym 0xffe3, [COLOR="#FF0000"]Control_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 40, synthetic NO, window 0x6600001,
    root 0x295, subw 0x0, time 4648162, (-293,159), root:(482,607),
    state 0x14, keycode 37 (keysym 0xffe3, [COLOR="#FF0000"]Control_L[/COLOR]), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

Okay, so it seems that xdotool uses the keys as laid out by **xev**. That's what I needed to know.

In that case, here's some code that gives "cleaner" output:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```

I came across it here: [https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys#In_Xorg](https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys#In_Xorg)

---

### Post by vasa1 on 2014-01-23
@stinkeye, could you explain why you used **xev &** rather than plain **xev**? Both seem to do the job.

I found > If a command is terminated by the control operator &, the shell executes the command in the background in a subshellbut I'm none the wiser :(

---

### Post by stinkeye on 2014-01-23
> **vasa1 said:**
> @stinkeye, could you explain why you used **xev &** rather than plain **xev**? Both seem to do the job.

I found but I'm none the wiser :(

Was using so the terminal would stay open when xev was closed but doesn't seem to matter.
Don't need the &

That codes a good find....going in my notes. :)
Came across these also...
```
xmodmap -pke
sudo dumpkeys -l
```

---

