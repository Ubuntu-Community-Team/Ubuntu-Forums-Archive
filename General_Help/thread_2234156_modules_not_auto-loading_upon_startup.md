---
title: "modules not auto-loading upon startup"
date: 2014-07-12
forum: General Help
---

### Post by aramil248 on 2014-07-12
so i followed this post to get my joystick working [http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457) and it works until i reboot then i have to manually load the modules to use my joystick again. can i get some help please?

---

### Post by varunendra on 2014-07-13
Have you added the module names to /etc/modules file as mentioned in the guide post you linked to?

What exactly do you need to do to make it work? If it is just the "modprobe" commands, then adding them to the /etc/module file should have worked.

---

### Post by aramil248 on 2014-07-13
yup i followed the whole guide and i still need to do "sudo modprobe sidewinder" to use the joystick.

---

### Post by varunendra on 2014-07-13
Before running the 'modprobe..' command, please post the outputs of -
```
cat /etc/modules
dmesg | grep sidewinder
```

..or maybe post back ALL the steps you took while following the guide, so we can see if you implemented everything correctly. That guide you followed is too old. I didn't read it very carefully, but it is possible that some of its steps may be outdated and not applicable today (like I am not sure with the stuff about '/etc/modules.conf' file).

---

### Post by aramil248 on 2014-07-13
```
 # /etc/modules: kernel modules to load at boot time.#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


## Pilotes de manette de jeu (joystick)
joydev         ## Module for gamepads
ns558          ## Module for gameport
sidewinder     ## Module for MS-SideWinder pads 
```

nothing happens when i type [COLOR=#000000][FONT=Ubuntu Mono]dmesg | grep sidewinder[/FONT][/COLOR]

---

### Post by varunendra on 2014-07-13
I think the 'joydev' and 'ns558' modules are not meant for you, they are for different game controllers. Try removing those entries (or commenting them out by adding a hash (#) at the beginning of those lines), then reboot and check -
```
lsmod | grep sidewinder
```
..to see if the module loaded automatically.

And when you load it manually (if still required after the above change), check "dmesg | grep sidewinder" AFTER that also. Any error messages?

---

### Post by aramil248 on 2014-07-13
ok i did what you said and i still had to manually load it. "[COLOR=#000000]dmesg | grep sidewinder" showed nothing.[/COLOR]

---

### Post by varunendra on 2014-07-14
Can I see the output of -
```
cat /etc/module
```please?

And for a test, please try -
```
sudo sed -i '/^exit 0/i sleep 6 && modprobe sidewinder' /etc/rc.local
```
..followed by a reboot. After reboot, check if it loaded automatically this time -
```
lsmod | grep sidewinder
```

Although the above is not a good way to automate the loading, but if the test succeeds, we can make it better. If it fails, try changing the 'sleep' time to '10' (even worse, but just for a test) by following command -
```
sudo sed -i '/sidewinder/ s/6/10/' /etc/rc.local
```
Then reboot and check "lsmod | grep sidewinder" again. Loaded ?

---

