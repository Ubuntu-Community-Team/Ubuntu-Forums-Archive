---
title: "How keep screen on during feh slideshow?"
date: 2024-08-10
forum: General Help
---

### Post by Alex_K. on 2024-08-10
Hello,

the question is in the title.

I'll just add some context. I have a bunch of family photos. I'd like those to be displayed in the slideshow format, sometimes. I'm using feh for running the slideshow. But here's the issue - since I'm basically leaving my PC to run feh "in background" (not bash background, I just leave my keyboard and mouse, while slideshow is running on my screen) after the predetermined time - the screen goes blank and computer locks.

Now, I'd rather strongly prefer not altering idle/lock/sleep timeouts at the global system basis. I don't think it's justified, for occasional slideshow. I do believe it can be achieved exempting  a certain command from these, on user choice basis, rather I don't know how, hence the question. I tried to uses systemd-inhibit to no avail - the system still locks, even when running this with sudo (I do know it's really not recommended from security standpoint, I tried it just to be sure systemd-inhibit isn't permissions inhibited). Just one last thing - I'd rather prefer native bash solution, than some side PPAs or python scripts occasionally moving the mouse. So, how keep screen on during feh slideshow?

Thank you!

---

### Post by Holger_Gehrke on 2024-08-10
You forgot to mention what version and flavour of Ubuntu you're using. Also the GUI stack in use - X11 or Wayland - is quite important.
For example in Xubuntu on X11 there is a power management plugin that can be put in (one of) your panel(s) that has an option for 'Presentation Mode'. As long as that option is set, no screen saver will ever start.

Holger

---

### Post by Alex_K. on 2024-08-10
> **Holger_Gehrke said:**
> You forgot to mention what version and flavour of Ubuntu you're using. Also the GUI stack in use - X11 or Wayland - is quite important.
For example in Xubuntu on X11 there is a power management plugin that can be put in (one of) your panel(s) that has an option for 'Presentation Mode'. As long as that option is set, no screen saver will ever start.

Holger

You're right. The system is Ubuntu 22.04.4 (LTS) with Wayland.

---

### Post by currentshaft on 2024-08-10
.

---

### Post by #&amp;thj^% on 2024-08-10
Maybe this?
```
 apt show wdisplays 
Package: wdisplays
Version: 1.1.1-1build2
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Sway and related packages team <team+swaywm@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 162 kB
Depends: libc6 (>= 2.34), libcairo2 (>= 1.10.0), libepoxy0 (>= 1.0), libglib2.0-0t64 (>= 2.79.0), libgtk-3-0t64 (>= 3.23.1), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libwayland-client0 (>= 1.20.0)
Homepage: https://github.com/artizirk/wdisplays
Download-Size: 46.5 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
[B]Description: graphical application for configuring displays in Wayland compositors
 wdisplays is a graphical application for configuring displays in Wayland[/B]
 compositors. It borrows some code from kanshi. It should work in any compositor
 that implements the wlr-output-management-unstable-v1 protocol, including sway.
 The goal of this project is to allow precise adjustment of display settings in
 kiosks, digital signage, and other elaborate multi-monitor setups.


```

---

### Post by Alex_K. on 2024-08-10
> **currentshaft said:**
> I don't use Wayland, but perhaps xset could work?

xset s off -dpms

Thank you, but I rather not change system wide settings (as far as I understand xset) for sake of 1 particular program. I'm looking for disabling screen/computer lock temporarily, hopefully from bash for a particular bash command, feh in my instance (hence it should expire once feh closes).

---

### Post by Alex_K. on 2024-08-10
> **1fallen said:**
> Maybe this?
```
 apt show wdisplays 
Package: wdisplays
Version: 1.1.1-1build2
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Sway and related packages team <team+swaywm@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 162 kB
Depends: libc6 (>= 2.34), libcairo2 (>= 1.10.0), libepoxy0 (>= 1.0), libglib2.0-0t64 (>= 2.79.0), libgtk-3-0t64 (>= 3.23.1), libpango-1.0-0 (>= 1.20.0), libpangocairo-1.0-0 (>= 1.14.0), libwayland-client0 (>= 1.20.0)
Homepage: https://github.com/artizirk/wdisplays
Download-Size: 46.5 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
[B]Description: graphical application for configuring displays in Wayland compositors
 wdisplays is a graphical application for configuring displays in Wayland[/B]
 compositors. It borrows some code from kanshi. It should work in any compositor
 that implements the wlr-output-management-unstable-v1 protocol, including sway.
 The goal of this project is to allow precise adjustment of display settings in
 kiosks, digital signage, and other elaborate multi-monitor setups.


```

Thank you. Unfortunately I could not find a man page for wdisplays. While Ubuntu repository copy, seems to be maintained by Ubuntu Developers, this seems to be the GitHub page of the project: [https://github.com/artizirk/wdisplays](https://github.com/artizirk/wdisplays) and if I understand it correctly, unfortunately it doesn't supposed to keep a screen on, for a duration of some random (feh, in my instance) bash command.

While feh code does not prevent the screen from locking, Firefox code on the other hand - does (while playing). Is it an OS feature or end program (feh/firefox) feature? Meaning, keeping the PC from locking, should be added to feh code or OS recognition of slideshow running? How other s/w does it? Maybe that worth investigating. Anyhow, I'd rather prefer bash option if somebody is aware of.

---

### Post by currentshaft on 2024-08-10
.

---

### Post by #&amp;thj^% on 2024-08-10
> **Alex_K. said:**
> Anyhow, I'd rather prefer bash option if somebody is aware of.

No wayland here XFCE4 but what is returned from:
```
ls /sys/class/drm

```

EDIT: for a bash script it seems like this would work, but not very elegant:
```
apt search wlr-randr 
wlr-randr/oracular 0.3.0-1 amd64
  Utility to manage outputs of a Wayland compositor

```
If I used wayland I could help a little better, but something like:
```
wlr-randr --output DP-1 --off ## or on
```
More found here: [https://manpages.debian.org/testing/wlr-randr/wlr-randr.1.en.html](https://manpages.debian.org/testing/wlr-randr/wlr-randr.1.en.html)

---

### Post by HermanAB on 2024-08-11
Here is my solution for X using xdotool.  Wayland has a similar ydotool:
[https://www.aeronetworks.ca/2014/06/mouse-wiggler.html?m=1](https://www.aeronetworks.ca/2014/06/mouse-wiggler.html?m=1)

---

