---
title: "no keyboard layouts to choose from"
date: 2006-11-29
forum: General Help
---

### Post by armware on 2006-11-29
running kde on 6.10

my keyboard works (minus the multimedia keys, but i can fix those again) however i cannot select a keyboard layout as there are zero to choose from. i'm assuming this broke when i upgraded from 6.06 because that's when my volume control buttons stopped working and i finally got around to looking at the keyboard configs. that's when i discovered i had zero layouts. this should be simple, but i'm at a loss.
ideas?

sorry - i just realized this should be in the 'upgrade' section. my bad. that's what i get for not paying attention to what tab i'm in.

---

### Post by ingo on 2006-12-01
what have you tried so far? Been in System Settings - Regional & Accessability - Keyboard Layout?

---

### Post by armware on 2006-12-01
it occurred to me that this happened after i upgraded to 6.10, so i moved it to the install/upgrades section:
[http://ubuntuforums.org/showthread.php?t=309424](http://ubuntuforums.org/showthread.php?t=309424)

to answer your question, that is where i have zero layouts to choose from. i have an image in my post on the above link. thanks for your time. my question appears to be uninteresting to everyone else.

---

### Post by ingo on 2006-12-03
ok, no idea what might be happening there. You could, however, add extra keyboard layouts via /etc/X11/xorg.conf

Here is the relevant section of my file:

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

To add extra layouts separate them with a comma. Don't ask me how to choose between them though, as I did the above method with xfce4, where a keyboard layout switcher depended on those settings.

---

### Post by armware on 2007-01-16
never did figure this out, but there was much broken anyways, so i did a complete wipe/reinstall. i wanted to redo the partitioning anyways, so i just took the opportunity and went for it. thanks, though.

---

### Post by ingo on 2007-01-17
why don't you post the relevant bit of your /etc/X11/xorg.conf (the generic keyboard bit) - is it different to mine?

(just out of interest...)

---

### Post by armware on 2007-01-17
i'd love to, but it's gone. i repartitioned and reinstalled from kubuntu 6.10 disc and i have my layouts back.

on a side note i am relatively familiar with the xorg.conf file and most of its settings and when i looked at it nothing seemed out of the ordinary.

i tried numerous things, regenerating locales, reinstalling xserver-kbd (or whatever it is), dpkg-reconfigure xserver-xorg, nothing helped. i ended up with quite a few issues at that point as i had installed ubuntu 5.05, upgraded to 5.10, installed kubuntu-desktop, then upgraded to 6.06, then 6.10 and that's probably why things got pretty messed up. thanks for your replies, though. i really do appreciate it.

upon reinstalling i finally got to experience first hand how nice linux is to reinstall and get everything set back up the way i had it, it only took about an hour to repartition, reinstall, and reconfigure everything i needed. i love how much of my settings are saved in my home directory. that made it a snap to get it back how i liked it, minus of course a few other things.

thanks again, i wish i had the time to spend trying to fix it so we could have a solution for anyone else with the same problem, but i have a 5 year old and a pregnant soon to be wife, so i really just needed it working properly quickly.

---

