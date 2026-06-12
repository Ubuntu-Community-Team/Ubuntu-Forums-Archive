---
title: "Ubuntu 17.10 Wayland-Gnome Tweaks. Disable touchpad while typing does not work"
date: 2018-02-15
forum: General Help
---

### Post by sab432 on 2018-02-15
Hi,

I have a small laptop and often during typing, my palm hits the touchpad. On ubuntu 17.10 tweaks, there is an option to set this to true. I have set disable touchpad while typing to true, yet the touchpad works even during the typing. Is this a bug ? How can I correct this.

---

### Post by DuckHook on 2018-02-15
I haven't installed Artful on any of my laptops, but turning on *disable touchpad while typing* on a Xubuntu Xenial install behaves as follows:

[list]
[*]The mouse delays moving for about a second. I have to continually swipe the touchpad before it eventually "kicks in".
[*]Although the above behaviour stops mouse movement while I am typing, if I pause typing for more than a couple of seconds, mouse will activate from inadvertent palm pressure.
[/list]
Both behaviours are irritating. However, I don't know how it can be designed any better. In order to give the opportunity to start typing, that initial pause is needed. But in order to reconnect mouse movement to the touchpad, it must assume that a pause in typing of a certain length constitutes suspension of typing. I don't know where I can tweak these settings, and it hasn't bothered me enough to motivate me to chase down the settings location.

Are your symptoms the result of pauses in typing?

Aside from above, I can't really help. I don't have any laptops running Artful or Wayland.

---

### Post by sab432 on 2018-02-17
> **DuckHook said:**
> I haven't installed Artful on any of my laptops, but turning on *disable touchpad while typing* on a Xubuntu Xenial install behaves as follows:

[LIST]
[*]The mouse delays moving for about a second. I have to continually swipe the touchpad before it eventually "kicks in". 
[*]Although the above behaviour stops mouse movement while I am typing, if I pause typing for more than a couple of seconds, mouse will activate from inadvertent palm pressure. 
[/LIST]
Both behaviours are irritating. However, I don't know how it can be designed any better. In order to give the opportunity to start typing, that initial pause is needed. But in order to reconnect mouse movement to the touchpad, it must assume that a pause in typing of a certain length constitutes suspension of typing. I don't know where I can tweak these settings, and it hasn't bothered me enough to motivate me to chase down the settings location.

Are your symptoms the result of pauses in typing?

Aside from above, I can't really help. I don't have any laptops running Artful or Wayland.

Hi, thanksfor the reply.I test the functionality simply by moving my touch pointer while pressing keys. I also have similar problem with Ubuntu Xenial/XOrg where I tried to disable while typing using libinput. The problem in that was that my Xorg/udev detected touchpad as a pointer. I suspect that the problem with touch pad settings not getting applied is basically still because of touchpad getting detected as a pointer. Its not just that, even the webcam gets detected as a keyboard. I dont know if I should file bug report or consult other forums. Could you point me to some ways? Here is my output to 

```
libinput-list-devices

```

```

Device:           HAILUCK CO.,LTD Usb Touch
Kernel:           /dev/input/event5
Group:            5
Seat:             seat0, default
Capabilities:     pointer 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   button
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   flat *adaptive
Rotation:         n/a

Device:           USB 2.0 Camera: USB 2.0 Camera
Kernel:           /dev/input/event14
Group:            6
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a
```

---

### Post by DuckHook on 2018-02-17
Searching provided this recent thread that might help: [https://ubuntuforums.org/showthread.php?t=2379851](https://ubuntuforums.org/showthread.php?t=2379851)

---

