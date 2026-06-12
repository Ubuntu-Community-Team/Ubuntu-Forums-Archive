---
title: "dvorak-qwerty available on linux?"
date: 2007-07-13
forum: General Help
---

### Post by cleverselfreferentialname on 2007-07-13
In Mac OS X, there is a keymap called dvorak-qwerty, wherein the keyboard would be qwerty for as long as you held ctrl. This was incredibly useful in that you're able to use the old keyboard shortcuts, ctrl+d, ctrl+z/x/c/v, in their QWERTY positions even though you're typing dvorak.

Does anyone know of something like this on linux? I really like dvorak, but I don't want to relearn all the keyboard shortcuts.

---

### Post by der_joachim on 2007-07-14
I have a KDE applet which allows me to switch keyboard layouts on the fly. Another option is to assign a shortcut to switch your layout in your xorg.conf. Make sure that your keyboard looks something like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle" 
EndSection

```
This way, pressing Alt+Shift will switch layouts.

---

### Post by alexmoon on 2007-09-29
I had this installed, then it just suddenly...stopped working. I press both my 'shift' keys, and it just stays in dvorak. This is a real problem because my other layout it greek, which I *need*. 

I can't figure out why, since I don't think I changed anything recently that would have affected this. I can't even figure out what to try out. Any ideas would be greatly appreciated!

---

### Post by shingalated on 2007-09-29
No idea how to fix the scripts, but can you change it back through System>Preferences>Keyboard

---

### Post by alexmoon on 2007-09-29
I kind of need to be able to switch back and forth quickly. Will be pretty cumbersome to do it through the preferences when I am typing out word lists and such. Thanks for the suggestion, though.

---

### Post by der_joachim on 2007-09-30
> **alexmoon said:**
> I kind of need to be able to switch back and forth quickly. Will be pretty cumbersome to do it through the preferences when I am typing out word lists and such. Thanks for the suggestion, though.

KDE has an applet with which you can change layouts with a single mouse click. So does Gnome probably. Do you want something like that perhaps?

---

### Post by alexmoon on 2007-09-30
I'll have a look for it, thanks. I don't really get why shift-shift stopped working, though. And I can't seem to get the greek layout working now, even through system -> preferences -> keyboard -> keyboard layout. It's all a bit weird.

---

### Post by alexmoon on 2007-09-30
Ok, the greek-dvorak problem is solved. Turned out it should have read "gr", not "greece". Of course, the mystery remains of why "greece" worked for weeks, then. I guess maybe the name was changed or something. Odd.

---

