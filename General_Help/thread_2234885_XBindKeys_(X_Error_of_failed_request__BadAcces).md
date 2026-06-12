---
title: "XBindKeys (X Error of failed request:  BadAcces)"
date: 2014-07-17
forum: General Help
---

### Post by Oasu4g on 2014-07-17
Hey guys,

Can anyone tell me why I'm getting this error after running ```
xbindkeys -v
```?

```
xbindkeys -vdisplayName = :0
rc file = /home/tim/.xbindkeysrc
rc guile file = /home/tim/.xbindkeysrc.scm
getting rc guile file /home/tim/.xbindkeysrc.scm.
initializing guile fns...
xbindkey_wrapper debug: cmd=xbindkeys_show.
xbindkey_wrapper debug: modifier = control.
xbindkey_wrapper debug: modifier = shift.
xbindkey_wrapper debug: key = q
xbindkey_wrapper debug: cmd=xterm.
xbindkey_wrapper debug: modifier = alt.
xbindkey_wrapper debug: modifier = m:4.
xbindkey_wrapper debug: modifier = mod2.
xbindkey_wrapper debug: key = c:0x29


min_keycode=8     max_keycode=255 (ie: know keycodes)
"xbindkeys_show"
    Control+Shift + q
"xterm"
    m:0xc + c:41
[B]X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  33 (X_GrabKey)
  Serial number of failed request:  15
  Current serial number in output stream:  19[/B]
```

I'm having trouble getting xbindkeys to respond to anything after configuration, and I'm thinking this has everything to do with it.

Thanks for any input you might have.

Regards

---

