---
title: "French, US, and German Keyboard how to toggle"
date: 2007-11-22
forum: General Help
---

### Post by regines on 2007-11-22
Hi all 
here at the campus in Bordeaux we have Ubuntu, me too 7.10 Gutsy,
Gnome off course.
in Kde, Solaris, Irix or vapourware, there was somwere a flag and
 the keybord could be toggled from one layout to another and vice versa.

Ihave to write Lyx Latex and Scribus some hundred pages a mix of French, 
german and US... The Notes

So how to toggle easy between the three to have the right letters
in my text:guitar:

---

### Post by der_joachim on 2007-11-22
There's two ways that I know of, a keyboard layout applet and tweaking xorg.conf. I am not a gnome user so I cannot help you there. Both xfce and KDE have standard applets so I can only assume that Gnome has one as well...

As for xorg: I use qwerty and dvorak. My keyboard section in /etc/X11/xorg.conf looks like this:
> 
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
Option         "XkbOptions" "grp:alt_shift_toggle,compose:ralt,eurosign:5,altwin:super_win"
EndSection

The alt_shift_toggle xkb option enables me to switch layouts on the fly by pressing Alt+Shift. Very annoying when in certain programs, but invaluable in login screens. Since you use french letters with accents a lot, you may alse like the compose:ralt-option: your right alt becomes a compose key which enables you to press RAlt+'+e to get an é.

---

### Post by mikewhatever on 2007-11-22
The default keyboard combination is alt+alt. The applet is called Keyboard Indicator. It is in Utilities of the Add to Panel.

---

