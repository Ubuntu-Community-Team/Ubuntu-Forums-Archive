---
title: "button bindings only for mouse - not touchpad"
date: 2015-08-19
forum: General Help
---

### Post by benuix on 2015-08-19
Hi all,

I'm trying to setup my mouse buttons.
Is there a way to setup bindings that will work only for mouse and not for the touchpad?
I have tried with xbindkeys but it works for both which is annoying.

My .xbindkeysrc looks like the following:
```

"xdotool keydown ctrl keydown shift key Tab keyup ctrl keyup shift"
   m | m:0x0 + b:6

"xdotool keydown ctrl key Tab keyup ctrl"
   m | m:0x0 + b:7

```

Thank you!

---

