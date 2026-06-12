---
title: "Keycodes with xev"
date: 2007-05-14
forum: General Help
---

### Post by atomic_turtle on 2007-05-14
Hi,

I've got a new keyboard, the MMNEK4000, and I'm just trying to configure all the Internet- and Media-Keys and, while I'm at it, I'd also like to reconfigure some of the regular keys that I just find a bit awkward for typing, like the @ - okay on an English keyboard, a good finger exercise on a German one and the '- it's too close to the Backspace key.
So, to this end, I've installed xev to first find out all the key-codes. That's no problem for most keys. I've only come across two questions here:

1) How can I find out what keycodes the "regular" keys (letters, numbers, the keys you'd find on a typewriter) send when pressed together with Shift, Alt or Ctrl._ When using xev, I only get the keycode of Alt and the (same) keycode of whichever regular keys I press, nothing different.

2) Is there any way of getting those keys to work which do not send a keycode that xev can recognize? There are way too many of those on this keyboard for my liking - not really surprising given it's a Microsoft keyboard, but really annoying, especially as the entire num_block seems to be among them.

Thanks a lot!

Regards,

atomic_turtle

P.S.: I don´t see any easy way to close a thread, but this is fixed: The number pad works after the latest update and I learnt there is only one keycode - in the xmodmap several keysyms can be written behind every keycode to account for the modifier keys.
Thread closed.

---

