---
title: "Alternative way to write 5 and %"
date: 2008-03-04
forum: General Help
---

### Post by Fnugbatter on 2008-03-04
The 5-key on my laptop is broken so I can't write 5 and %

Does anyone know of a way to write 5 by for instance pressing Alt Gr and z ?

---

### Post by danwood76 on 2008-03-04
You can remap keys using the xmodmap comand and xev to find key codes.
To find out the mapping of keys do:
```

xmodmap -pke

```
I would save this list just incase you need to restore the original mapping of a key.
but the important like is the one containing the 5 percent etc.
```

keycode  14 = 5 percent onehalf threeeighths onehalf threeeighths

```
So if I wanted F10 to become my 5 key, first start xev
```

xev

```
then press F10, when you press the key you will get output in the terminal like this:
```

KeyPress event, serial 31, synthetic NO, window 0x4200001,
    root 0x87, subw 0x0, time 2048589355, (467,464), root:(475,514),
    state 0x0, **keycode 76** (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4200001,
    root 0x87, subw 0x0, time 2048589451, (467,464), root:(475,514),
    state 0x0, **keycode 76** (keysym 0xffc7, F10), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
the important part is the keycode (bold above)
then use the xmodmap command to remap the key.
```

xmodmap -e "keycode 76 = 5 percent onehalf threeeighths onehalf threeeighths"

```
The keycode is the keycode above (F10) and the stuff after the = is what the key does.

then the F10 key will be the 5 key, you obviously want to choose a key you dont use as this will completely replace its functionality.
I think using the F keys is a bad idea as they often do stuff in laptops (and in linux)

hope this helps,
Danny

---

### Post by Fnugbatter on 2008-03-04
Thank you :)

I just made Caps Lock useful for the first time ever!

By adding
```
xmodmap -e "clear Lock"
```
I got rid of it's ability to upper/lowercase

---

