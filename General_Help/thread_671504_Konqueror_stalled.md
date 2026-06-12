---
title: "Konqueror stalled?"
date: 2008-01-18
forum: General Help
---

### Post by superbenny on 2008-01-18
I just did a clean install of Kubuntu 7.04 (I prefer it to 7.10, so don't try to tell me I should upgrade because it will solve my problems...it just made more)

When I open up Konqueror, I can't see any of my files. In the status bar at the bottom it says No Items - No Files - No Folders, then changes to Stalled. I can clearly see the files in Konsole, but nowhere else. When I try to open something in GIMP, nothing. Opening a local theme in Superkaramba? Nothing. Just a little bar that says 0%. I can't see any files, no matter what folder I'm in. I used to be able to log out and back in, and that would solve it. But now even that isn't working...which is extremely odd. Please help, I'm going insane not being able to open anything.

---

### Post by Christmas on 2008-01-18
Do you get a 'Malformed URL' error when you start Konqueror? Have to tried to remove it and install again or delete the configuration files (~/.kde/share/config/konquerorrc and ~/.kde/share/apps/konqueror)? Try remove those (the latter is a directory) and see what happens when you start Konqueror again. If not, try to launch it without any parameters (hit ALT+F2 and type 'konqueror' without the quotes).

---

### Post by superbenny on 2008-01-18
No errors other than 'Stalled"

When i try to 'Open' anything in Gimp, openoffice, etc, it cant read any files

---

### Post by Christmas on 2008-01-18
Please provide more information. Hit Alt+F2 and type konsole, then enter 'konqueror'. What is the output of the command?

Try also to update your packages
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by superbenny on 2008-01-18
> **Christmas said:**
> Please provide more information. Hit Alt+F2 and type konsole, then enter 'konqueror'. What is the output of the command?

Try also to update your packages
```
sudo apt-get update && sudo apt-get upgrade
```
konqueror

outputs


X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
and opens konqueror

---

### Post by superbenny on 2008-01-19
bump

can someone please help?

---

