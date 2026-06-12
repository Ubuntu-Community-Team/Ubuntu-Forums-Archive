---
title: "Complete lockup at the computer but SSH access available?"
date: 2013-03-29
forum: General Help
---

### Post by Ranko Kohime on 2013-03-29
I've run into a weird situtation.  I was attempting to start a game via Steam.  The game crashed and took the window manager (Cinnamon) with it.  Cinnamon reloaded, so I tried again.  Same thing, but Cinnamon did not come back up.

Ctrl+Alt+F1 and I killed the remnants of Cinnamon, and tried to restart it with cinnamon --replace.  I've had an on-again/off-again issue with the display variable, and exporting DISPLAY=:0 doesn't solve it, so I wasn't able in this case to restart Cinnamon.

So I decide to kill and restart gdm.  Well, this appeared to switch me back to the desktop pane, (F7), except all the pre-GUI status reports were there.  Then it was completely locked up at the keyboard.  I could not switch back to F1, or any of the other TTY's.  I could, however, login via SSH, so I did, and rebooted.

Upon reboot however, I was met with the same issue.  Prior to when the login screen would normally come up, it locks up, and is only accessible via SSH.  F8 does not switch between status and boot logo as normal, and no TTY can be accessed.

Setup: Lenovo Thinkpad E420, (integrated graphics, so my drivers are not at issue) Ubuntu 12.10, installed from the network CD, with first Gnome 3, and then Cinnamon as my WM.

ETA: When rebooting there is no warning echoed to the local screen, it just suddenly blanks out.

---

### Post by Ranko Kohime on 2013-03-29
As an update, I occasionally run this setup via VirtualBox under a Windows 7 host, whenever a long off-site file backup is going and I wish to play games.  I booted up in the VM, and it started up and logged in just fine.  Rebooting, however, presented me with the same problems as before.

---

### Post by Ranko Kohime on 2013-04-02
For the benefit of future Goolgers, I had added the xorg-edgers ppa, and updated all the packages, and then forgot about it for several weeks until I had to reboot.  Purged the ppa and updated packages, and all is well.

---

