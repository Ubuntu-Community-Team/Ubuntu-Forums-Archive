---
title: "keyboard types incorrect characters"
date: 2019-05-16
forum: General Help
---

### Post by satimis on 2019-05-16
Ubuntu 16.04

Hi all,

For unknown reason my keyboard types incorrect characters. I have not touched the settings nor anything.

Reboot, shutdown, restart did not help. Then after restart on terminal I run

&#10219; setxkbmap it

&#10219; locale```

LANG=en_HK.UTF-8
LANGUAGE=en_HK:en
LC_CTYPE="en_HK.UTF-8"
LC_NUMERIC="en_HK.UTF-8"
LC_TIME="en_HK.UTF-8"
LC_COLLATE="en_HK.UTF-8"
LC_MONETARY="en_HK.UTF-8"
LC_MESSAGES="en_HK.UTF-8"
LC_PAPER="en_HK.UTF-8"
LC_NAME="en_HK.UTF-8"
LC_ADDRESS="en_HK.UTF-8"
LC_TELEPHONE="en_HK.UTF-8"
LC_MEASUREMENT="en_HK.UTF-8"
LC_IDENTIFICATION="en_HK.UTF-8"
LC_ALL=

```

Then I can type correct characters and numbers but I could not type correct symbols such as / ) ? (  etc.

Change the keyboard from another computer does not help.

Please help

Thanks in advance.

Edit-1
====
After reboot I have to run
&#10219; setxkbmap it
again.

Otherwise the keyboard cannot type correct characters and numbers.  But still I could not type correct symbols.

Edit-2
====
I found the solution

&#10219; setxkbmap us   # type "us" instead of "it"
&#10219; locale```

LANG=en_US.UTF-8
LANGUAGE=en_US:en_GB:en_AU:en_CA:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=en_HK.UTF-8
LC_TIME=en_HK.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=en_HK.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=en_HK.UTF-8
LC_NAME=en_HK.UTF-8
LC_ADDRESS=en_HK.UTF-8
LC_TELEPHONE=en_HK.UTF-8
LC_MEASUREMENT=en_HK.UTF-8
LC_IDENTIFICATION=en_HK.UTF-8
LC_ALL=

```

Then keyboard can type correct characters, numbers and symbols.  But still after reboot I have to run the command again.

I don't know why and how this problem happens ??????


Regards
satimis

---

### Post by rsteinmetz70112 on 2019-05-16
If you have a graphic desktop go to "Settings" and change it there.  It's somewhat different in different window managers 

To run from a command line (terminal)
```
sudo dpkg-reconfigure console-data
```
If console-date is not installed
```
sudo apt install console data
```
It should run the configuration, if not run the first command.

---

### Post by satimis on 2019-05-16
> **rsteinmetz70112 said:**
> If you have a graphic desktop go to "Settings" and change it there.  It's somewhat different in different window managers 

To run from a command line (terminal)
```
sudo dpkg-reconfigure console-data
```
- snip- 
Hi,

Thanks for your advice.

$ sudo dpkg-reconfigure console-data
select [Don't touch keymap]

Reboot.  It is still the same and I have to run```

&#10219; setxkbmap us
```
on Terminal

Just found that the keyboard worked properly for a new user.

Created a new user satimisliu.  After login the keyboards worked properly without problem.

I don't know WHY and HOW it happens to user satimis ?

This PC has been working for several years without problem.  About 5~6 months ago I replaced the old SSD-HD (1TB) with a new SSD-HD (2TB).  It also works without problem until yesterday.

I'm at lost !!!!!!

Regards
satimis

---

### Post by #&amp;thj^% on 2019-05-16
Login to the "satimis" account and Check current layout and options:
to see current:
```

setxkbmap -print -verbose 10
```

Reset layout to US and reset options:

```
setxkbmap -layout us
``` 
If using a variant (e.g. intl), try

```
setxkbmap -layout us -variant intl
```
or:
```
setxkbmap -layout us -variant intl
```
If still no joy try adding this to your Startup applications:
```
/bin/bash -c "sleep 15&&setxkbmap -layout us -option ctrl:nocaps"
```

---

### Post by satimis on 2019-05-17
> **1fallen said:**
> Login to the "satimis" account and Check current layout and options:
to see current:
```

setxkbmap -print -verbose 10
```

Reset layout to US and reset options:

```
setxkbmap -layout us
``` 
If using a variant (e.g. intl), try

```
setxkbmap -layout us -variant intl
```
or:
```
setxkbmap -layout us -variant intl
```
If still no joy try adding this to your Startup applications:
```
/bin/bash -c "sleep 15&&setxkbmap -layout us -option ctrl:nocaps"
```
Hi,

Thanks for your advice

login satimis

The keyboard is in completely disorder, not working properly.

&#10219; setxkbmap -print -verbose 10```

Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc101
layout:     fr,us
variant:    ,
Trying to build keymap using the following components:
keycodes:   evdev+aliases(azerty)
types:      complete
compat:     complete
symbols:    pc+fr+us:2+inet(evdev)
geometry:   pc(pc101)
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(azerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+fr+us:2+inet(evdev)"        };
        xkb_geometry  { include "pc(pc101)"     };
};

```


Why ?```

layout:     fr,us

```

```

setxkbmap -layout us

```
can´t work

```

&#10219; setxkbmap -layout us -variant intl

```
works.  Keyboard works correctly.

&#10219; setxkbmap -print -verbose 10```

Setting verbose level to 10
locale is C
Trying to load rules file ./rules/evdev...
Trying to load rules file /usr/share/X11/xkb/rules/evdev...
Success.
Applied rules from evdev:
rules:      evdev
model:      pc101
layout:     us
variant:    intl
Trying to build keymap using the following components:
keycodes:   evdev+aliases(qwerty)
types:      complete
compat:     complete
symbols:    pc+us(intl)+inet(evdev)
geometry:   pc(pc101)
xkb_keymap {
        xkb_keycodes  { include "evdev+aliases(qwerty)" };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc+us(intl)+inet(evdev)"       };
        xkb_geometry  { include "pc(pc101)"     };
};

```

```

layout:     us

```

Logout satimis and relogin
The keyboards is in disorder again.

Where is Startup Application?  I can´t find it on System Settings

Edit
===
After login satimis

There is a small icon on the right top-menu bar
English US
(check) French

Change it to
(check) English US
French

Then the keyboard works correctly.

Regards
satimis

---

