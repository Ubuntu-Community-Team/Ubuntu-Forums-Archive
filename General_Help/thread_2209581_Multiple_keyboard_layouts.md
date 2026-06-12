---
title: "Multiple keyboard layouts"
date: 2014-03-06
forum: General Help
---

### Post by Fake51 on 2014-03-06
Just upgraded to ubuntu 13.10 to have that out of the way when 14.04 comes.

I am working with an Apple keyboard, which for unknown reasons has alt/cmd keys switched (and a few other weird things). In 13.04 I used setxkbmap to set the settings I needed to have the keyboard work as normal - however, with 13.10 there's apparently some monitoring going on that resets the keyboard layout on any process switch. Which means I can happily type away in one window, use alt+tab to switch to another window, then try using alt+tab to switch back, only to realize that ubuntu has reset the changes made by setxkbmap.

My problem is that I use different keyboards: the apple keyboard and the native laptop keyboard. When the apple keyboard is attached that should be the active configuration - otherwise the native keyboard should be. I don't mind switching manually between the two, but I'll be damned if I have to change settings through a menu that's five clicks away. It's a computer and it's supposed to be used for automating stuff.

So, I'm looking for solutions that will let me use both keyboards (obviously not at the same time) without having to run scripts every time I switch windows.

---

### Post by Fake51 on 2014-03-07
Also, if anyone has any inside information on what happened to the general keyboard options present in 13.04 and previous (it was possibly to make a lot of changes to keyboard layout, including switching keys, etc).

This seems to have gone the way of the dodo as well - anyone know why or how to get it back?

I've seen advice to use gnome-tweak-tool - but on my install like on so many others it crashes and burns without letting me do anything.

---

### Post by Fake51 on 2014-03-19
So, managed to figure out a solution. For anyone stuck with the same problem, this might help.

It's possible to change xbk-options using gsettings - directly modifying essentially the same settings that you would modify with setxkbmap. The difference being, Ubuntu doesn't crap all over your changes but respects them.

So, my script to change layout now contains commands like

```
# switch layout to Apple keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle","altwin:swap_lalt_lwin","altwin:swap_ralt_rwin","apple:alupckeys"]'

# switch layout to normal keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle"'
```

I run the script with a parameter to switch either one or the other layout, and detect keyboards using one of lsusb/lsinput/udevadm

---

### Post by Fake51 on 2014-07-30
Aaaaaand another update as, once again, with a system update, some moron decided to break what was working just fine. It seems as though whichever developer is in charge of input methods never conceived of the idea that somewhere, someone might actually use different keyboards with the same computer.

Anyway, for 14.04, this now works:

```
# switch layout to Apple keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle","altwin:swap_alt_win","altwin:swap_ralt_rwin","apple:alupckeys"]'

# switch layout to normal keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle"]'
```

---

### Post by Fake51 on 2014-08-07
> **Fake51 said:**
> Aaaaaand another update as, once again, with a system update, some moron decided to break what was working just fine. It seems as though whichever developer is in charge of input methods never conceived of the idea that somewhere, someone might actually use different keyboards with the same computer.

Anyway, for 14.04, this now works:

```
# switch layout to Apple keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle","altwin:swap_alt_win","altwin:swap_ralt_rwin","apple:alupckeys"]'

# switch layout to normal keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle"]'
```

I did not do enough testing with the above. To make it work properly, that is, to swap left alt and super keys, while at the same time swapping right super with alt +gr (NOT ALT!!), use:

```
# switch layout to Apple keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle","altwin:swap_alt_win","lv3:ralt_switch","apple:alupckeys"]'

# switch layout to normal keyboard
/usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle"]'
```

---

### Post by Fake51 on 2015-03-18
By request here's the combination I use to switch things at startup, depending on presence of my apple keyboard

1. a script running at startup to detect what's plugged in. This is just run from .zprofile (seeing as I'm running zsh. .profile or any other of the typical solutions for running a script at startup would also work). I have a terminal starting automatically when I login so .zprofile will get executed - if you don't, use another solution, like just adding a startup script.

> #!/bin/bash
APPLE_PRESENT=`/usr/bin/lsusb | /bin/grep 'Apple, Inc. Aluminium Keyboard'`
if [ ! -z "$APPLE_PRESENT" ]
then
    /usr/local/bin/switch-keyboard.sh apple
else
    /usr/local/bin/switch-keyboard.sh
fi

sleep 10

TIMES=$1

if [ -z "$TIMES" ]
then
    TIMES=1
fi

if [ $TIMES -ge 5 ] 
then
    exit 0;
else
    TIMES=$((TIMES+1))

    $0 $TIMES
fi

2. the script that actually changes settings looks like this

> #!/bin/bash

if [ "$1" = "apple" ]
then
    # set the Apple keyboard
    /usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle","altwin:swap_alt_win","lv3:ralt_switch","apple:alupckeys"]'
else
    # set the normal keyboard
    /usr/bin/gsettings set org.gnome.desktop.input-sources xkb-options '["grp:lalt_lshift_toggle"]'
fi

---

