---
title: "is there a problem with compose key in 24.04 in LXDE?"
date: 2024-09-27
forum: General Help
---

### Post by shantiq on 2024-09-27
using[ this]("https://ubuntuforums.org/showthread.php?t=2236007&p=13083189#post13083189") which always worked previously ***in LXDE*** but not in 24.04 for me
any ideas?


thanx

added info & **EDIT** (as often the mistake/"fault" was mine and mine only :)



I had toggled/unclicked    [[IMG]https://i.postimg.cc/nC8pMzRh/Screenshot-from-2024-09-28-08-22-01.png[/IMG]]("https://postimg.cc/nC8pMzRh") by inadvertence   


 after i have set ```
setxkbmap -option "compose:rwin"
```
```
sudo leafpad /etc/default/keyboard
``` gives me  

```
# KEYBOARD CONFIGURATION FILE


# Consult the keyboard(5) manual page.


XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS="compose:rwin"






BACKSPACE="guess"
```




AND THEN:   



```
setxkbmap -print -verbose 10

```   gives me


```
setxkbmap -print -verbose 10Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc105
layout:     gb,ru
variant:    ,
[COLOR=#000000]***options:    grp:lwin_toggle,compose:rwin***[/COLOR][COLOR=#006400]***          which is the correct options lwin for switch between RU and EN and lwin is now my Compose Key a key not needed/used in Ubuntu as it is for a Windows set-up***[/COLOR]
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+gb+ru:2+inet(evdev)+compose(rwin)+group(lwin_toggle)
geometry:   pc(pc105)
xkb_keymap {
    xkb_keycodes  { include "evdev+aliases(qwerty)"    };
    xkb_types     { include "complete"    };
    xkb_compat    { include "complete"    };
    xkb_symbols   { include "pc+gb+ru:2+inet(evdev)+compose(rwin)+group(lwin_toggle)"    };
    xkb_geometry  { include "pc(pc105)"    };
};



```


MARKED as Solved



**Example:**

[COLOR=#0C0D0E][FONT=-apple-system]now I press rwin and **release** then click on "o c" to obtain **© é è ü &#8364; **[/FONT][/COLOR]**&#281;¡ë **[COLOR=#0C0D0E][FONT=-apple-system]**etc etc **[/FONT][/COLOR]

---

