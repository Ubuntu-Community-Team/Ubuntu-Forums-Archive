---
title: "Ubuntu 18.04 LTS: can't compose with system (super/left-window/menu) key"
date: 2018-09-11
forum: General Help
---

### Post by MgFrobozz on 2018-09-11
I just installed ubuntu 18.04 LTS. Under versions 12, 14, and 16, I'd installed the keyboard "English (intl., with AltGr dead keys), and used the keyboard to compose foreign keys (eg, hitting system-'-a to compose a long a for Hungarian). That combination no longer works.

I'm running gnome flashback, so I installed and then ran gnome-tweaks, selecting the "Keyboard & Mouse" tab. I made sure that "Compose Key" was enabled, then selected "Menu", but it didn't work (for the key sequence above, I got two characters, acute-accent and 'a'). I tried logging out and logging back in (didn't work). I tried this change in /etc/default/keyboard, using the value for the key from /usr/share/X11/xkb/rules/base.lst (didn't work):

```
[COLOR=#000000]XKBOPTIONS="compose:lwin"[/COLOR]
```

I tried logging out and logging back in again (didn't work), I tried this command, which reportedly forces the change without a logout/login (didn't work):

```
[COLOR=#000000]udevadm trigger --subsystem-match=input --action=change[/COLOR]
```

I found that all of the other selections in gnome-tweaks _do_ work when selected from gnome-tweaks, and take effect immediately. The choices are confusing: gnome-tweaks calls the right system/super/window key "Right Super", but it doesn't offer "Left Super" as a choice, instead offering "Menu". I don't know whether "Menu" is yet another alias for system/super/window; if it's not, I have no idea which key "Menu" is. 

Any advice on how to get the former default for the compose key (left system/super/window/menu) working again?

---

### Post by lashi on 2019-03-13
I can second this. Here's some of my data. 
> 
XKBOPTIONS="compose:lwin,terminate:ctrl_alt_bksp"


Now, I've tried looking at the event generation in xev, and actually, there is a composition but then it's dropped. Here's the output:

> 
KeyPress event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1230828, (849,498), root:(857,592),
    state 0x0, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: True

KeyPress event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1230976, (849,498), root:(857,592),
    state 0x0, keycode 48 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XmbLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: True

KeyRelease event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1231050, (849,498), root:(857,592),
    state 0x0, keycode 48 (keysym 0x27, apostrophe), same_screen YES,
    XLookupString gives 1 bytes: (27) "'"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1231100, (849,498), root:(857,592),
    state 0x0, keycode 133 (keysym 0xff20, Multi_key), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1231274, (849,498), root:(857,592),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XmbLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: True

KeyPress event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1231274, (849,498), root:(857,592),
    state 0x0, keycode 0 (keysym 0xe1, aacute), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 2 bytes: (c3 a1) "á"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4600001,
    root 0x13f, subw 0x0, time 1231377, (849,498), root:(857,592),
    state 0x0, keycode 38 (keysym 0x61, a), same_screen YES,
    XLookupString gives 1 bytes: (61) "a"
    XFilterEvent returns: False


But for some reason, this doesn't seem to generate á in the key composition.

---

### Post by lashi on 2019-03-13
Also, I should note that when you switch to the console via Ctrl+Alt+F1, then compose key *does* work!

---

### Post by lashi on 2019-03-14
POTENTIAL FIX: 

So, it seems that my compose key issues have gone away. What I have done is to remove the fcitx packages. In terms of the stuff that I have for input, here's my list when I do dpkg -l | grep input: 

```

ii  inputattach                                1:1.6.0-2                                 amd64        utility to connect serial-attached peripherals to the input subsystem
ii  libinput-bin                               1.10.4-1                                  amd64        input device management and event handling library - udev quirks
ii  libinput10:amd64                           1.10.4-1                                  amd64        input device management and event handling library - shared library
ii  xinput                                     1.6.2-1build1                             amd64        Runtime configuration and test of XInput devices
ii  xserver-xorg-input-all                     1:7.7+19ubuntu7.1                         amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev                   1:2.10.5-1ubuntu1                         amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-libinput                0.27.1-1                                  amd64        X.Org X server -- libinput input driver
ii  xserver-xorg-input-synaptics               1.9.0-1ubuntu1                            amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-wacom                   1:0.36.1-0ubuntu1                         amd64        X.Org X server -- Wacom input driver

```

Also, I installed ibus: 
```

ii  gir1.2-ibus-1.0:amd64                      1.5.17-3ubuntu4                           amd64        Intelligent Input Bus - introspection data
ii  ibus-gtk:amd64                             1.5.17-3ubuntu4                           amd64        Intelligent Input Bus - GTK+2 support
ii  ibus-gtk3:amd64                            1.5.17-3ubuntu4                           amd64        Intelligent Input Bus - GTK+3 support
ii  im-config                                  0.34-1ubuntu1.2                           all          Input method configuration framework
ii  libibus-1.0-5:amd64                        1.5.17-3ubuntu4                           amd64        Intelligent Input Bus - shared library
ii  libxi6:amd64                               2:1.7.9-1                                 amd64        X11 Input extension library
ii  xinput                                     1.6.2-1build1                             amd64        Runtime configuration and test of XInput devices

```


In diagnosing the problem, I actually noticed that compose key works fine in the console (Ctrl+Alt+F2) and also at the lightdm login screen. It only fails to work when MATE/LXDE etc loads. 

I compared this list which I've given above to my Ubuntu 18.04 system where compose key does work - this was an upgrade from 16.04 compared to this fresh install. The main difference was the existence of this fcitx packages. 

Hope this helps.

---

