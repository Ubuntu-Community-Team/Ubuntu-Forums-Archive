---
title: "Samsung Keyboard Brightness Keys"
date: 2014-05-05
forum: General Help
---

### Post by aaaaaaaadam.s on 2014-05-05
So I've recently installed Ubuntu 14.04 (kernel: 3.13.0-24-generic). It's mostly working with my Samsung NP540U4E laptop, just having some trouble with the keyboard brightness change function keys. ```
dmesg | grep -i setkeycodes
``` shows me that the scancodes are e017 for brightness down (Fn + F9) and e016 for brightness up (Fn + F10). ```
xmodmap -pke
```gives me the output (among other things)```
keycode 237 = XF86KbdBrightnessDown NoSymbol XF86KbdBrightnessDown
keycode 238 = XF86KbdBrightnessUp NoSymbol XF86KbdBrightnessUp
``` which I think are correct commands because ```
xdotool key XF86KbdBrightnessDown
xdotool key XF86KbdBrightnessUp
``` change the keyboard brightness up and down. I then tried ```
sudo setkeycodes e017 237
sudo setkeycodes e016 238
``` which did not make the keys work to increase or decrease keyboard brightness but it did prevent additional errors in dmesg when I hit the buttons. There is nothing registered with acpi_listen or xev when the keys are pressed, both before and after setkeycodes. However it does seem that F10 (without function pressed) is already mapped to keyboard brightness up as pressing it increases keyboard brightness. Hopefully I've included enough information and thanks in advance for any help.

---

### Post by aaaaaaaadam.s on 2014-05-07
Realised that for some reason I have to subtract 8 from the keycodes to get them to work but now I have another problem. My laptop doesn't register these keys being released so they both only work once as it thinks they are still held. And I couldn't see a scancode for the release of the keys

---

