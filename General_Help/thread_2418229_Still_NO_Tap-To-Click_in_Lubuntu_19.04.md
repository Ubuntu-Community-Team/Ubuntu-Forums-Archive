---
title: "Still NO Tap-To-Click in Lubuntu 19.04"
date: 2019-05-03
forum: General Help
---

### Post by stoc2528 on 2019-05-03
I've been avoiding each version of Lubuntu because I can never get Tap-To-Click enabled on my laptops.  I saw a post on Reddit where a dev said it would be fixed in 19.04 but there's still no tap-to-click.

Is there anyway to enable tap-to-click for touchpads in Lubuntu?

Thanks,

---

### Post by #&amp;thj^% on 2019-05-03
I can't imagine that this wouldn't work (it worked in 18.10): (But I don't use Lubuntu)

Create a file using the command below:
```

sudoedit  /etc/X11/xorg.conf.d/30-touchpad.conf
```

Paste the following:
```

Section "InputClass"
    Identifier "devname"
    Driver "libinput"
    Option "Tapping" "on"
EndSection

```
device id  can be seen with:
EDIT: After a quick re-read I should mention 'devname' will most likely be "TouchPad "
```
# xinput list
```
Mine looks like this:
```
&#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
```
Reboot and you should have working tap to click with two finger context menu.
See this for the concept: [https://wiki.archlinux.org/index.php/Libinput#Touchpad_configuration](https://wiki.archlinux.org/index.php/Libinput#Touchpad_configuration)

---

### Post by linucksrox on 2019-05-09
1fallen, thanks! I just tried that method on Lubuntu 19.04 and it worked nicely. I didn't reboot since I'm running a live session from USB, but I just need to log out and log back in for the change to take effect.

---

