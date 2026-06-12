---
title: "weird capslock issue"
date: 2018-06-29
forum: General Help
---

### Post by cmcanulty on 2018-06-29
I am running xubuntu 16.04. I have caps lock disabled. However lately caps lock turns on and won't turn off. If I log out or restart capslock is off as I have disabled it. How can I troubleshoot this? Thank you.

---

### Post by #&amp;thj^% on 2018-06-29
Please add how you have "caps lock disabled">>meaning is there any extra actions taken by you?
Or simply just not pressed by keyboard.

Try creating the file **10-nocaps.conf **with the following content:

```
Section "InputClass"
        Identifier             "keyboard-layout"
        MatchIsKeyboard        "on"
        Option "XkbOptions"    "ctrl:nocaps"
EndSection

```
...and place it in either** /etc/X11/xorg.conf.d **or **/usr/share/X11/xorg.conf.d** (depending on which folder your distro uses) and log out and back in again to test.

I picked this up from ToZ a few years back.

---

### Post by cmcanulty on 2018-06-29
Yes I tried 2 permanent fixes see screenshot for the one from settings manager and a command  line fix I added to startup apps  

```
xmodmap -e "clear Lock" -e "keysym Caps_Lock = Escape"
```

[ATTACH=CONFIG]280245[/ATTACH]

---

### Post by #&amp;thj^% on 2018-06-29
seems to me that both conflict with each other. try removing the "xmodmap -e "clear Lock" -e "keysym Caps_Lock = Escape" from autostart.
If no joy then try the script I show in my prior post.

---

### Post by cmcanulty on 2018-06-29
OK will do.Have to wait until it occurs again to post result, thank you!

---

