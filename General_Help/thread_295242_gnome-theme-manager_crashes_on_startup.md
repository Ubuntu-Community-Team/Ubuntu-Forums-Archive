---
title: "gnome-theme-manager crashes on startup"
date: 2006-11-07
forum: General Help
---

### Post by MikeMLP on 2006-11-07
Greetings.  I am using edgy, I have beryl installed (although this happens whether it is turned on or not) and I also have KDE installed as well.

Whenever I go to system->preferences->theme, the gnome-theme-manager starts up, displays question mark icons in place of the theme icons, and usually crashes immediately (It closes on its own, but the process remains and I have to kill it manually as it eats up 100% cpu cycles).  This problem seemed to start right after I installed beryl (back then, compiz).  if the program doesn't crash immediately, when I try to scroll through the themes, the window freezes, resulting in tiled text and icons (like if you have a frozen window and you drag it around the screen and it leaves a trail of window images).  If I start from the terminal, I get the following:

```
:~$ gnome-theme-manager
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I also get a similar messages when starting beryl, although once it starts up, beryl works fine.  Any ideas to restore functionality?  packages to reinstall, files to remove?

Thanks!

---

