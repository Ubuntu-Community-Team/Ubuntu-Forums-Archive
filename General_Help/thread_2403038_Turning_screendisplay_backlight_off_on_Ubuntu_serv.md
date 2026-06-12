---
title: "Turning screen/display backlight off on Ubuntu server"
date: 2018-10-06
forum: General Help
---

### Post by elufkin on 2018-10-06
I have a laptop computer running as a server. The screen backlight does not seem to turn off by itself when the keyboard or mouse is inactive.

I can turn the backlight off using "vbetool dpms off", but I would like to have it turn off automatically after a preset time, and turn back on automatically when local keyboard or mouse activity is detected.

What's an elegant way to accomplish this? :confused:

OS: Ubuntu 18.04 LTS Server x64

---

### Post by Holger_Gehrke on 2018-10-06
Take a look at 'setterm'. On my machine this sequence```
setterm --powersave powerdown
setterm --powerdown 2
```on a virtual console will turn both my displays (internal and external) off after two minutes of inactivity.

Holger

---

### Post by elufkin on 2018-10-07
```
--powersave powerdown
              Puts the monitor into VESA powerdown mode.
```

Ok. That makes sense.

```
# setterm --powersave powerdown
setterm: cannot (un)set powersave mode: Inappropriate ioctl for device
```

But I get this error.

I'm doing this through SSH. Maybe this need to be issued on the local ttys?

---

### Post by Holger_Gehrke on 2018-10-07
As I said, it works in a virtual console on my machine. It does not work - actually gives the exact same error you got - from an xterminal or an xfce4-terminal. Since both of those connect to /dev/pts/n instead of a real terminal device on /dev/ttyn, that's probably the problem. I think it does need to be called from the terminal for which one is trying to set those options.

Holger

---

### Post by elufkin on 2018-10-07
How would I save these settings permanently?

The idea is when the server is done booting up and nobody is logging in, then the screen shuts off after a preset time.

---

