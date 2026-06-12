---
title: "disable mouse pointer / cursor"
date: 2021-03-06
forum: General Help
---

### Post by Regexaurus on 2021-03-06
I'm using LXQt on Lubuntu 20.04.2 LTS, and would like to disable the mouse pointer / cursor. I added the -nocursor option in /etc/X11/xinit/xserverrc, so the exec line is now:
```
exec /usr/bin/X -nocursor -nolisten tcp "$@"
```
saved my changes, and rebooted. This made no difference.
 I prefer to disable the cursor using X server options and not use unclutter. If you know how to do this, I would appreciate your help! :D

---

### Post by Regexaurus on 2021-03-08
For other users of the interwebs looking for the same, edit /etc/sddm.conf, add a section as shown below, save and reboot.

$ sudo vim (or nano, etc.) /etc/sddm.conf

new section:

```
[X11]
ServerArguments=-nocursor -nolisten tcp
```

Save changes

$ reboot now

I don't know if ServerArguments options are additive/cumulative to options found in /etc/X11/xinit/xserverrc, or if this replaces the arguments. I initially assumed replacement, and had set ServerArguments to '-nocursor -nolisten tcp "$@".' After rebooting, the GUI didn't complete loading. I used the Ctrl+Alt+F2 shortcut to login a text-only environment, modify /etc/sddm.conf, removing "$@" from ServerArguments, and reboot. I'm unsure of the purpose of "$@."

I found this helpful: [https://wiki.archlinux.org/index.php/SDDM](https://wiki.archlinux.org/index.php/SDDM)

---

### Post by Regexaurus on 2021-03-08
/etc/X11/xinit/xserverrc is apparently a shell script, and $@ would be an array containing arguments passed to the script. Just a *guess*, but this *probably* means ServerArguments you specify in sddm.conf are eventually passed as arguments to xserverrc. If so, including "-nolisten tcp" in ServerArguments is redundant. Of course, adding -nocursor to xserverrc apparently did nothing (see initial post)... :-k

---

