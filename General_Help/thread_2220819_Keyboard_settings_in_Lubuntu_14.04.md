---
title: "Keyboard settings in Lubuntu 14.04"
date: 2014-04-29
forum: General Help
---

### Post by fugazi32 on 2014-04-29
Hi, as the Lubuntu keyboard manager keeps changing back to American default keyboard on rebooting I edited my */etc/default/keyboard* file to:

```

# If you change any of the following variables and X is configured to
# use this file, then the changes will become visible to X only if udev
# is restarted.  You may need to reboot the system.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=","
XKBOPTIONS="grp:ctrl_shift_toggle,grp_led:scroll"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.

```

I wanted a UK keyboard but still get an American one each time I boot up :(

---

### Post by bapoumba on 2014-04-29
Can you right click on the Keyboard layout Handler and go to Settings ?
This worked for me on this fresh install. The keyboard was set to us, note quite practical on an azerty one :)

---

### Post by fugazi32 on 2014-05-02
Nope, that only gives me the option for a Dvorak UK keyboard which types out gibberish. Any ideas?

Will the 'UK Dead Keys' work, whatever that is??

---

### Post by bapoumba on 2014-05-02
Can you "Add" ?

---

### Post by fugazi32 on 2014-05-02
Can only seem to add the normal UK keyboard layout via Lxkeymap (which doesn't seem to save setting on reboot) - only Dvorak/Dead Keys show up for UK keyboard settings...

---

### Post by bapoumba on 2014-05-02
That is quite strange, here are all the options I can choose from.

---

### Post by syntaxerror74 on 2014-07-15
This stuff must be insanely buggy in 14.04.

From some certain point (system crash) I'm now having the same problem.

To begin with, lxkeymap will *heavily* interfere with Keyboard Layout Handler, so using both is not recommended at all.
Second, unticking "Keep system layouts" in Keyboard Layout Handler will never be permanent, but left side will always be greyed out after logon. I'm about to get desperate, since I don't know how to get these settings permanent.

Currently, I always have US keyboard layout after logon and I have to start lxkeymap ONCE (and close it again) to get my local layout. It's the horror.
And yes, I have the correct layout set in /etc/default/keyboard as well, but it's completely ignored.

---

### Post by bapoumba on 2014-07-15
Anything in /etc/xdg/lxsession/Lubuntu/desktop.conf ?
Here is mine :
```
[Keymap]
mode=system
model=
layout=
variant=
options=
```

With /etc/default/keyboard
```
# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="fr"
XKBVARIANT="latin9"
XKBOPTIONS="compose:lwin"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
```

Would you have removed ibus ?

---

### Post by syntaxerror74 on 2014-07-15
> Anything in /etc/xdg/lxsession/Lubuntu/desktop.conf ?
Here is mine :
...

Looks exactly the same. *mode=system* and the rest is unset.
But thanks for trying to help.

> Would you have removed ibus ?
No, not removed, just left unassigned. However it seems independent of the defaulting to US layout.
In Language Support->Language, I've set keyboard input method system to 'none'.
But this is for something else, in fact to circumvent this extremely annoying GEdit bug:[URL="https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1299759g:"]
[/URL][https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1299759](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1299759)[URL="https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1299759g:"]
[/URL]

---

### Post by bapoumba on 2014-07-15
Yeah. Not using gedit, but ibus messes around with Chromium..
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

---

### Post by syntaxerror74 on 2014-07-15
> **bapoumba said:**
> Yeah. Not using gedit, but ibus messes around with Chromium..
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

*shrug*
Well, I'm a happy Firefox user. \\:D/

---

### Post by bapoumba on 2014-07-15
> **syntaxerror74 said:**
> *shrug*
Well, I'm a happy Firefox user. \\:D/

So did I become when using lubuntu :)
Whichever works best.

---

