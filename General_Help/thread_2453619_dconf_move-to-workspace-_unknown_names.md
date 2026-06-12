---
title: "dconf move-to-workspace-? unknown names"
date: 2020-11-13
forum: General Help
---

### Post by sombunall on 2020-11-13
OS:  Ubuntu 20.04

I am trying to use dconf editor (keybindings) to allow moving applications to workspaces beyond the default 4. I can do it with Shift+Super+pagedown but I want to use numbers. Dconf requires me to somehow know what to put for the shifted numbers. I've figured out everything but '^' caret, '(' left parenthesis, ')' right parenthesis. What are they called really? Where is the list?

I already expanded workspaces to 10 and made them static.

For example I have 8 working with a custom value ['<Shift><Super>asterisk']

---

### Post by sombunall on 2020-11-24
I searched the source of gnome-settings-daemon* and found no mention of the word 'asterisk'.

---

### Post by sombunall on 2020-11-24
I tried binary searching my bin directory:

$ find /usr/bin -exec bash -c 'if [[ $(strings {} | grep -i asterisk) ]]; then dpkg -S "{}"; fi' \;
strings: Warning: '/usr/bin' is a directory
gnome-calculator: /usr/bin/gnome-calculator
console-setup: /usr/bin/ckbcomp
strings: Warning: '/usr/bin/X11' is a directory
strace: /usr/bin/strace
xserver-xorg-input-wacom: /usr/bin/xsetwacom
python3-minimal: /usr/bin/python3
python3.8-minimal: /usr/bin/python3.8
patch: /usr/bin/patch
dpkg-query: no path found matching pattern /usr/bin/bash
usbutils: /usr/bin/lsusb
dpkg-query: no path found matching pattern /usr/bin/loadkeys
mc: /usr/bin/mcdiff
mc: /usr/bin/mcview
printer-driver-min12xxw: /usr/bin/min12xxw
aptitude: /usr/bin/aptitude-curses
dpkg-query: no path found matching pattern /usr/bin/rbash
x11-xkb-utils: /usr/bin/xkbprint
dpkg-query: no path found matching pattern /usr/bin/aptitude
mc: /usr/bin/mc
mc: /usr/bin/mcedit
dpkg-query: no path found matching pattern /usr/bin/dumpkeys
dpkg-query: no path found matching pattern /usr/bin/udevadm

Looked at x11-xkb-utils,  console-setup and still nothing. It's not parenleft, parenright or asciicirum or even dead_circumflex. I'm running out of ideas.

---

