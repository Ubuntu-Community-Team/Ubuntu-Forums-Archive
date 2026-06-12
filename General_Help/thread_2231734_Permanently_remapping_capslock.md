---
title: "Permanently remapping capslock"
date: 2014-06-27
forum: General Help
---

### Post by Biopyro on 2014-06-27
I am using the minimak layout which I love but I prefer to have caps lock remapped to backspace. Up until now I have been using 

```
xmodmap ~/.xmodmap
```


 
to run this code; manually when I boot. Recently though this has been resetting once every few minutes and it is infuriating. How can I prevent this or permanently remap capslock? There seems to be some provision to do this with evdev but I have no idea how to trigger it.


```
!! Make the caps lock button a backspace button
!
remove Lock = Caps_Lock
keycode 66 = BackSpace

```

I have tried using gnome tweak tool but this is unable to disable caps lock - it just makes it delete things as well! Installing it seems to have worsened the problem too as when xmodmap is modified it now won't do backspace with caps lock when shift is held.

thanks in advance!

---

### Post by buzzingrobot on 2014-06-27
If you are really running 11.04, this may be irrelevant, but...

Via dconf-editor, you can get at org.gnome.desktop.input-sources, where you will find an editable "xkb-options" field.  Now, I only use this to disable capslock altogether, by putting 'caps:none' in the field (with the quotes). You'd have to find the right lingo to map the key instead.

---

### Post by Biopyro on 2014-06-27
That seems to do the same thing that the gnome tweak tool option does.

I have a functional caps-lock key that is* also *a backspace key. It is unsurprisingly driving me a bit mad.


Edit: I turned off the tweak tool and just lived with xmodmap resetting so often. A few days later it stopped happening.

---

