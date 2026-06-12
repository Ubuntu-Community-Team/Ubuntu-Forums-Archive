---
title: "How to Turn On Touchpad, When It's Off: Without a Touchpad or Mouse"
date: 2023-09-06
forum: General Help
---

### Post by webmanoffesto on 2023-09-06
When I have no mouse and the Touchpad is turned off, how can I turn on Touchpad, if in order to do that I need a mouse or a touchpad. 

I'm on an HP Laptop and I often use it with a mouse and turn off the touchpad.
But then I pick up the laptop and take it to a place, and I have to work without a mouse, and the touchpad is turned off.
But to turn on the touchpad I need a mouse to navigate the "Settings / Mouse and Touchpad" menu.
A couple of times I was able to keep clicking Tab until I got to the correct location, but that stopped working. That's also hard to do when the Settings window opens in a weird location, like half off screen.
What's a solution for this problem?

Ubuntu 22

---

### Post by Rubi1200 on 2023-09-06
Hi,

Open a terminal with Ctrl+Alt+T and run this command:

```
xinput list
```

This will display a list of your input devices, including touchpad. You are looking for something that includes Synaptic or Touchpad in the name.

Once you have identified the device ID you can turn it on or off using these commands:

```
xinput disable 12
```

or
```
xinput enable 12

```
Let us know if it works.

---

### Post by Holger_Gehrke on 2023-09-06
One small addition to Ruby1200's post:

The numeric id that 'xinput list' prints is not guaranteed to stay the same from one boot to the next. If you want to script activation / deactivation of devices you are better of using the names instead of the numbers.

Example:
```

$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=14    [slave  pointer  (2)]
.
.
.

$ xinput disable 14                           # switch touchpad off, but the number will not be the same every time

$ xinput enable 'ETPS/2 Elantech Touchpad'    # Switch touchpad on using the name which does stay the same

```

Holger

---

### Post by webmanoffesto on 2023-09-06
Which of these is the touchpad? I tried "2" but something's not working.

$ xinput list
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:16                         id=6    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:16                id=7    [slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:16                id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; xwayland-keyboard:16                        id=9    [slave  keyboard (3)]
$ xinput set-prop 2 "Device Enabled" 1
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
$ xinput enable 2
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
$ xinput enable 2
WARNING: running xinput against an Xwayland server. See the xinput man page for details.
$ xinput set-prop 2 "Device Enabled" 1
WARNING: running xinput against an Xwayland server. See the xinput man page for details.

What's with the Wayland Server? Is that because I explored KDE desktop? This still looks like an Ubuntu interface.

---

### Post by #&amp;thj^% on 2023-09-07
Here is a very nice guide to help with that: [https://www.baeldung.com/linux/enable-disable-touchpad](https://www.baeldung.com/linux/enable-disable-touchpad)
Please read the whole page.

---

### Post by Holger_Gehrke on 2023-09-08
> **webmanoffesto said:**
> 
What's with the Wayland Server? Is that because I explored KDE desktop? This still looks like an Ubuntu interface.

Wayland is a new Display Protocol that replaces the older - much older - X11 / xorg. X11 was designed in the early 80s of the last century and has a lot of capabilities that modern programs don't use (instead of telling the server to do things - like drawing lines, curves, patterns, text etc they do these things themselves - or use various libraries to do them - and send a finished bitmap to the server). Wayland cuts out all that cruft and makes for a much smaller and lighter server. It also fixes a lot of security problems that couldn't be fixed on X11 since they were part of the design (example: system wide input event queue that everything could listen in on - great for automation tools or global hotkeys, but horrible from a security point of view).

'xwayland' is a compatibility layer which runs for applications which 'talk' the older protocol that doesn't give these programs access to actual hardware but virtualizes everything so none of the devices you're seeing in 'xinput list' is actually the touchpad, it's just a generalized virtual pointing device. Since you're getting a new instance of xwayland for every X11 based program you're running, making settings on Wayland using X11 based tools usually doesn't work or at least doesn't work reliably. 

Both Gnome - the GUI of standard Ubuntu - and KDE can run with Wayland and will do so by default. You should have the option to select what Display Server you want to use at login (a cog icon on the login screen should become available after entering your user name and will show a menu with the available session types). Since Wayland leaves a lot of the stuff that used to be done by the server to the client, each Desktop Environment uses different tools for making settings. So in Gnome you will use gsettings - as the article that 1fallen linked to explained - and something else in KDE or Sway or Hyprland or in XFCE once that can use Wayland (important to me, since I'm using that ...). So Wayland - which was meant to simplify things - actually makes things more complicated on the command line ...

Holger

---

### Post by Rubi1200 on 2023-09-09
Based on something that happened to me recently...

Although you don't say what model HP laptop you have this might be worth a try:

Many HP laptops have a dedicated key combination to enable or disable the touchpad. Look for a key with an icon that resembles a touchpad or mouse. It's often in the F1 to F12 row, and you may need to press it in combination with the "Fn" (function) key. For example, it might be "Fn + F6" or "Fn + F12." Pressing this combination should toggle the touchpad on and off.

---

