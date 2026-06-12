---
title: "Swapping Ctrl and Cmd"
date: 2006-10-30
forum: General Help
---

### Post by theshibboleth on 2006-10-30
I would like to map the cmd (Apple) key on my Apple keyboard as ctrl and map ctrl as super, but I'm not sure how to do this. Any help appreciated.

It looks like this was asked before with no resolution ([http://ubuntuforums.org/showthread.php?t=48448&highlight=control+command)](http://ubuntuforums.org/showthread.php?t=48448&highlight=control+command)).

---

### Post by theshibboleth on 2006-10-31
Okay, I finally figured this out. Hopefully this will help someone else. Here's how you do it, assuming you have identical settings to me:

> xmodmap -e "remove mod4 = Super_L"
xmodmap -e "add control = Super_L Multi_key"
xmodmap -e "remove control = Control_L Control_R"
xmodmap -e "add mod4 = Control_L Control_R"


You can add each of those lines as startup programs so that the system will boot with these settings.

In case your keymap differs from mine, you can figure out what you need to do for your particular system by running 

> xmodmap -pm

This will tell you what keycodes are linked with what x-modifiers.

You can remove keycodes from x-modifiers by running

> xmodmap -e "remove X-MODIFIER = KEYCODE"

and you can add keycodes to x-modifiers by running

> xmodmap -e "add X-MODIFIER = KEYCODE"

Note: you must first remove a keycode from its current modifier before you can add it to another one. You can find the keycode for a key by running

> xev

and pressing the key.

---

