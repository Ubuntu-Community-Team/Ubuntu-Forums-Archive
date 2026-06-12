---
title: "Keyboard Layout Problem After Upgrading From Gutsy to Hardy"
date: 2008-05-03
forum: General Help
---

### Post by ade90212 on 2008-05-03
After upgrading my Gutsy Gibbon installation to Hardy Heron I found that my keyboard was set to en_US. Now, whenever I set the keyboard to gb in System --> Preferences --> Keyboard it works fin until I restart the computer and then it resets to the en_US layout.

I had a similar problem before when I upgraded from Feisty to Gutsy and I never resolved it satisfactorily and ended up doing a clean install of Gutsy, which worked perfectly.


Has anybody got any ideas as to how to make my prefered keyboard layout persist through a reboot? I would really rather not have to do a clean install.

---

### Post by Zorael on 2008-05-03
Try this. You'll likely lose any special videocard settings, but we'll make a backup so you can restore them manually afterwards.

Pop up a terminal and enter these commands.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```
It should ask you what layout you want, among some other things. Then restart X with Ctrl+Alt+Backspace.

---

### Post by ade90212 on 2008-05-04
After running ```
$ sudo dpkg-reconfigure xserver-xorg
``` and selecting the default options throughout the dialogue the following error message displayed when trying to restart the X Server:

> Faile to start the X Server. It is likely that it is not set up correctly. Would you like to vie the X Server output to diagnose the problem?

Clicking on yes gives the following: > Warning: Could not retrieve EDID because get-edid is not installed (1)

I've restored the original xorg.conf file but the keymap is still incorrect.

Does anyone else have any ideas?

---

### Post by Dyqik on 2008-05-04
The above solution worked for me (I didn't have an xorg.conf due to fiddling with autoconfig and hotplugging external displays to my laptop, so I didn't remove it).

I suggest fixing the missing get-edid problem first... (who knows when it will come back and bite you?)

A quick play suggests that the solution to the missing get-edid problem is to install the read-edid package in your favourite way.

---

### Post by ade90212 on 2008-05-05
I added the read-edid package as suggested but now when I run sudo dpkg-reconfigure xserver-xorg and restart X, the X Server still crashes but now when I click 'Yes' when asked whether I would like to view the X Server output, the output is blank.

---

### Post by ade90212 on 2008-05-05
Just in case anyone is interested, I "solved" this by replacing the whole /etc/X11 directory with the /etc/X11 directory from a live CD session. I did try replacing only the /etc/X11/xkb directory but this left me with the same problem.

---

### Post by Pablitox on 2008-05-07
I have the same issue, but I didn't upgrade, I made a fresh install. I couldn't solve the problem yet... :(

================================================================================================
EDIT:

SOLVED!!!
Just look for this section in your /etc/X11/xorg.conf:

```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
```Or similar and add this last line:

```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbLayout" "us,es"
```I just rebboted and that solved my problem!!!

---

### Post by MattiJ on 2008-05-16
Option         "XkbLayout" "us,se" did nor work for me but
Option         "XkbLayout" "se"

---

