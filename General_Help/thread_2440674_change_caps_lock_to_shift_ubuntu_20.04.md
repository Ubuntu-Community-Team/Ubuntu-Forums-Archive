---
title: "change caps lock to shift: ubuntu 20.04"
date: 2020-04-13
forum: General Help
---

### Post by icegood on 2020-04-13
Hi there. 

I'm trying to recall how my caps lock was disabled from previous version of ubuntu, since i've altered mine to 20.04  recently.
My new treats caps lock as caps lock and it kills me. 
I found settings in dconf-editor in
/org/gnome/desktop/input-sources/xkb-options branch to be:


['grp_led:scroll', 'caps:shift_nocancel', 'terminate:ctrl_alt_bksp', 'lv3:ralt_switch', 'compose:ralt']

but they don't seem to work.  

Thanks in advance.

---

### Post by norobro on 2020-04-13
I use xmodmap to disable the Caps Lock key. [https://linux.die.net/man/1/xmodmap](https://linux.die.net/man/1/xmodmap)

There are two ways you can go about changing it to shift:

[LIST=1]
[*]Create an .Xmodmap file in the users home directory containing:```
keycode 66 = Shift_L
```
[*]Enter the following in the user's .bashrc file: ```
xmodmap -e "keycode 66 = Shift_L"
```
[/LIST]
To disable the key use "keycode 66 ="

xmodmap is in the x11-xserver-utils package. [https://packages.ubuntu.com/focal/x11-xserver-utils](https://packages.ubuntu.com/focal/x11-xserver-utils)

---

### Post by DuckHook on 2020-04-13
I wrote a tutorial some months ago on key remapping: [https://ubuntuforums.org/showthread.php?t=2416537](https://ubuntuforums.org/showthread.php?t=2416537)

It addresses a different need but has general application.

---

### Post by Flimm on 2020-11-16
You can do this using GNOME Tweak tool. Install it using:

```
sudo apt install gnome-tweaks
```

Then click:

"Keyboard and Mouse", "Additional Layout Options" button, "Caps Lock behavior". To disable caps lock, choose "Caps Lock is disabled".

[IMG]https://i.stack.imgur.com/xSVcv.png[/IMG]

---

### Post by cybereality on 2021-05-25
Thanks Flimm. That works perfectly.

---

