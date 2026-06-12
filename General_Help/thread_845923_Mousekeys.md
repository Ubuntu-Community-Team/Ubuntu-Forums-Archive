---
title: "Mousekeys"
date: 2008-07-01
forum: General Help
---

### Post by petaloid on 2008-07-01
Hello all,
I've been trying out as many apps as I can to make my comp fully usable by keyboard but I am having trouble finding a way to toggle Mousekeys from the keyboard. Can I write a script to do that? Because if that is possible then I can set a shortcut to Xbindkeys.
Also I wish to remap the mousekey buttons. 

Thanks for your time.

---

### Post by petaloid on 2008-07-03
bump

anyone?

---

### Post by petaloid on 2008-07-03
bump... in the night

:/

---

### Post by schmick on 2008-09-23
ctrl-shift-numlock is the toggle combination for mousekeys.

---

### Post by zerem on 2009-11-20
--- as i posted in [https://bugs.launchpad.net/ubuntu/+bug/192508](https://bugs.launchpad.net/ubuntu/+bug/192508) ---

Hello fellow earthlings daily beaten by this bug.

I used this workaround to permanently disable mousekeys shortcut shift+num-lock, alt+shift+num-lock etc...

gksudo gedit /usr/share/X11/xkb/compat/complete
-or-
sudo nano /usr/share/X11/xkb/compat/complete

and comment out lines for mousekeys and accesx(full) (for full keyboard accessibility purge)

resulting file /usr/share/X11/xkb/compat/complete:
// $XKeyboardConfig$
// $Xorg: complete,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "complete" {
    include "basic"
    augment "iso9995"
    //augment "mousekeys"
    //augment "accessx(full)"
    augment "misc"
    augment "xfree86"
    augment "level5"
};

Wish you a lot happy days without moving mouse by keypad ;)
Greets Ondrej

---

