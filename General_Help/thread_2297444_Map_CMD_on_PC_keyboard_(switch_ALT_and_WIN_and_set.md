---
title: "Map CMD on PC keyboard (switch ALT and WIN and set “new WIN” as Meta)"
date: 2015-10-03
forum: General Help
---

### Post by univerzalni on 2015-10-03
[COLOR=#111111][FONT=Ubuntu]Is there an easy way to add CMD key to PC keyboard on Ubuntu?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Currently I have Slovenian (si) layout: [https://dl.dropboxusercontent.com/u/859847/si.png](https://dl.dropboxusercontent.com/u/859847/si.png)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
and would like to switch "Alt L" with "Super L" and also set "Super L" as Meta, so I could use Mac keymapped shortcuts on PHP Storm etc. (like on MacBook Air)[/FONT][/COLOR]

```
[COLOR=#111111][FONT=Ubuntu]setxkcmap -print[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu] currently shows:[/FONT][/COLOR]
```
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwertz)" };
    xkb_types     { include "complete"  };
    xkb_compat    { include "complete"  };
    xkb_symbols   { include "pc+si+us:2+inet(evdev)"    };
    xkb_geometry  { include "pc(pc105)" };
};
```

[COLOR=#111111][FONT=Ubuntu]I already tried to edit /usr/share/X11/xkb/symbols/pc and change LWIN and ALT + include "altwin(meta_alt)" to include "altwin(meta_win)", than clearing cache with ```
rm -rf /var/lib/xkb/*
``` but didn't work..[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
I also tried setting through ```
setxkbmap -option "altwin:swap_lalt_lwin, altwin:meta_win"
``` but couldn't get it work also..[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Any ideas for a permanent solution? It's a bit of an overkill to have to learn all the shortcuts for both Mac and Ubuntu in PHP Storm.. :)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Thanks in advance![/FONT][/COLOR]

---

