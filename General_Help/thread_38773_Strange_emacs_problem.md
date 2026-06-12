---
title: "Strange emacs problem"
date: 2005-06-01
forum: General Help
---

### Post by Penguin Man on 2005-06-01
I'm using Hoary with XFCE4 as my WM.  When using emacs (installed via apt-get emacs21), the standard M-x keystroke to execute a command seems to run make by default.  If I set M-x to execute-extended-command in my .emacs file, it decides that M-x is actually M-8 and doesn't do anything at all (except put whatever letter I type in 8 times).  It happens on my Ubuntu machines at home and at work, and also if I login remotely to a Sun machine at school from either of my Ubuntu machines and use emacs on it.  My guess is that it's a problem with X's keyboard mappings, but I can't figure out the problem.

Anyone have any ideas?  I really need M-x to work (those of you who use emacs will understand my frustration!).

---

### Post by Alexander Kirillov on 2005-06-02
[QUOTE=Penguin Man]I'm using Hoary with XFCE4 as my WM.  When using emacs (installed via apt-get emacs21), the standard M-x keystroke to execute a command seems to run make by default.  If I set M-x to execute-extended-command in my .emacs file, it decides that M-x is actually M-8 and doesn't do anything at all (except put whatever letter I type in 8 times).  It happens on my Ubuntu machines at home and at work, and also if I login remotely to a Sun machine at school from either of my Ubuntu machines and use emacs on it.  My guess is that it's a problem with X's keyboard mappings, but I can't figure out the problem.

Anyone have any ideas?  I really need M-x to work (those of you who use emacs will understand my frustration!).[/QUOTE]
 To see X kbd mapping, run (form command line) program xev and press Esc while mouse is xev window. It should produce somehting like this:
```

KeyRelease event, serial 29, synthetic NO, window 0x3000001,
    root 0x40, subw 0x3000002, time 604333222, (31,64), root:(498,596),
    state 0x10, keycode 9 (keysym 0xff1b, Escape), same_screen YES,
    XLookupString gives 1 bytes: (1b) ""

```
Important part is keycode 9 (keysym 0xff1b, Escape). If it gives something else, there is a problem with X keyboard mapping.

---

### Post by Penguin Man on 2005-06-15
xev doesn't return anything odd, however the problem does not happen when I use emacs on the commandline, so it does seem to be an X-related problem (especially since it does happen when I run emacs -nw - no gui - in an xterm but not on the commandline).

Edit: Even more odd, the problem only occurs if I run emacs -nw in an xterm.  If I run the gui version of emacs (still GNU emacs, not xemacs) it doesn't have a problem.  If I run emacs -nw in a gnome-terminal or an rxvt there's no problem.  Perhaps some sort of xterm problem.

---

### Post by Penguin Man on 2005-06-16
[QUOTE=Penguin Man]xev doesn't return anything odd, however the problem does not happen when I use emacs on the commandline, so it does seem to be an X-related problem (especially since it does happen when I run emacs -nw - no gui - in an xterm but not on the commandline).

Edit: Even more odd, the problem only occurs if I run emacs -nw in an xterm.  If I run the gui version of emacs (still GNU emacs, not xemacs) it doesn't have a problem.  If I run emacs -nw in a gnome-terminal or an rxvt there's no problem.  Perhaps some sort of xterm problem.[/QUOTE]
 I've solved the problem for now by just using rxvt instead of xterm.  Still interested to see what causes the problem though.

---

