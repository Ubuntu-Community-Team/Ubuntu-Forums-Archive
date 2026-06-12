---
title: "ir-keytable sees remote keys, xev does not"
date: 2023-03-03
forum: General Help
---

### Post by TheKorn2 on 2023-03-03
Hello,

brand new ubuntu 22.04.2 LTS install.


I have a mce remote and IR receiver. I do not have anything from lirc installed. After installing ir-keytable, if I do a sudo ir-keytable -t, and then hit any/every button on my remote, I see things like...

```

6477.546916: event type EV_KEY(0x01) key_up: KEY_ENTER(0x001c)
6477.546916: event type EV_SYN(0x00).
6477.992331: lirc protocol(rc6_mce): scancode = 0x800f0421 toggle=1
6477.992352: event type EV_MSC(0x04): scancode = 0x800f0421
6477.992352: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
6477.992352: event type EV_SYN(0x00).
6478.101263: lirc protocol(rc6_mce): scancode = 0x800f0421 toggle=1
6478.101271: event type EV_MSC(0x04): scancode = 0x800f0421
6478.101271: event type EV_SYN(0x00).
6478.235058: event type EV_KEY(0x01) key_up: KEY_RIGHT(0x006a)
6478.235058: event type EV_SYN(0x00).

```

So far so good -- ir-keytable is seeing every key on the remote. Problem is that many key presses aren't getting passed through to applications. (I'm using xev to show what events are being passed through.)

Some keys are showing in ir-keytable and xev:

```

161.098951: lirc protocol(rc6_mce): scancode = 0x800f041e
161.098975: event type EV_MSC(0x04): scancode = 0x800f041e
161.098975: event type EV_KEY(0x01) key_down: KEY_UP(0x0067)
161.098975: event type EV_SYN(0x00).
161.207789: lirc protocol(rc6_mce): scancode = 0x800f041e
161.207801: event type EV_MSC(0x04): scancode = 0x800f041e
161.207801: event type EV_SYN(0x00).
161.342244: event type EV_KEY(0x01) key_up: KEY_UP(0x0067)
161.342244: event type EV_SYN(0x00).

```

```

MappingNotify event, serial 37, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 37, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 161099, (107,125), root:(1723,285),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 161342, (107,125), root:(1723,285),
    state 0x0, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

MappingNotify event, serial 38, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

KeyPress event, serial 38, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 175900, (107,125), root:(1723,285),
    state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 39, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 176117, (107,125), root:(1723,285),
    state 0x4, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (03) ""
    XmbLookupString gives 1 bytes: (03) ""
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 176154, (107,125), root:(1723,285),
    state 0x4, keycode 54 (keysym 0x63, c), same_screen YES,
    XLookupString gives 1 bytes: (03) ""
    XFilterEvent returns: False

KeyRelease event, serial 39, synthetic NO, window 0x600001,
    root 0x77b, subw 0x0, time 176227, (107,125), root:(1723,285),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

And some keys are not, such as all the numeric keys on the remote (ir-keytable output only, as the event never gets passed to xev so there's no output):

```

315.584435: lirc protocol(rc6_mce): scancode = 0x800f0401 toggle=1
315.584459: event type EV_MSC(0x04): scancode = 0x800f0401
315.584459: event type EV_KEY(0x01) key_down: KEY_NUMERIC_1(0x0201)
315.584459: event type EV_SYN(0x00).
315.691312: lirc protocol(rc6_mce): scancode = 0x800f0401 toggle=1
315.691318: event type EV_MSC(0x04): scancode = 0x800f0401
315.691318: event type EV_SYN(0x00).
315.826227: event type EV_KEY(0x01) key_up: KEY_NUMERIC_1(0x0201)
315.826227: event type EV_SYN(0x00).
317.716516: lirc protocol(rc6_mce): scancode = 0x800f0402
317.716540: event type EV_MSC(0x04): scancode = 0x800f0402
317.716540: event type EV_KEY(0x01) key_down: KEY_NUMERIC_2(0x0202)
317.716540: event type EV_SYN(0x00).
317.823448: lirc protocol(rc6_mce): scancode = 0x800f0402
317.823455: event type EV_MSC(0x04): scancode = 0x800f0402
317.823455: event type EV_SYN(0x00).
317.958209: event type EV_KEY(0x01) key_up: KEY_NUMERIC_2(0x0202)
317.958209: event type EV_SYN(0x00).
318.737533: lirc protocol(rc6_mce): scancode = 0x800f0403 toggle=1
318.737557: event type EV_MSC(0x04): scancode = 0x800f0403
318.737557: event type EV_KEY(0x01) key_down: KEY_NUMERIC_3(0x0203)
318.737557: event type EV_SYN(0x00).
318.843446: lirc protocol(rc6_mce): scancode = 0x800f0403 toggle=1
318.843451: event type EV_MSC(0x04): scancode = 0x800f0403
318.843451: event type EV_SYN(0x00).
318.978197: event type EV_KEY(0x01) key_up: KEY_NUMERIC_3(0x0203)
318.978197: event type EV_SYN(0x00).
```


It's like something is swallowing them up.  I've already been in dconf-editor, /org/gnome/settings-daemon/plugins/media-keys and removed the default key mappings for things like play, pause, ff, rew, etc. and still these keys aren't being passed through.

How can I get ALL my keys passed through to xev (or any other program)?


------

I did see some searches about xorg not supporting keys above 255, but this behavior is identical whether I'm using xorg or wayland, so that can't be it.  (I'm using the 22.04 wayland default, but tried xorg just to make sure it wasn't that.)

---

### Post by DuckHook on 2023-03-04
> **TheKorn2 said:**
> …I did see some searches about xorg not supporting keys above 255, but this behavior is identical whether I'm using xorg or wayland, so that can't be it.  (I'm using the 22.04 wayland default, but tried xorg just to make sure it wasn't that.)
But why not? If xorg cannot support keys above 255 and neither will Wayland, then this may account for the problem.

I'm completely out of my depth with IR so what follows is purely hearsay try&#8209;at&#8209;your&#8209;own&#8209;risk type stuff, but I did find this in a websearch: [https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/](https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/)

:!: **CAUTION** :!:

I really, really don't like the idea of using a Xenial driver. It would be years out of date and could be totally compromised for all we know. But it doesn't seem to be a utility that requires deep system hooks, so it might not be too big a risk. The bigger risk may be that it will corrupt your install and render it unusable. As said, try at your own risk.

---

