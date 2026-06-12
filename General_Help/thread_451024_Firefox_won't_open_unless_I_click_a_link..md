---
title: "Firefox won't open unless I click a link."
date: 2007-05-21
forum: General Help
---

### Post by SZorg on 2007-05-21
Using Kubuntu

The only way I can get Firefox to open is by clicking a link in GAIM or Skype or another application. If I click on the icon or type it in to konsole, it pops up in the taskbar and the icon dances around my mouse pointer, but nothing opens. After about 20 seconds it disappears.

---

### Post by aysiu on 2007-05-21
Can you post the terminal output when you launch the command ```
firefox
``` from the Konsole?

---

### Post by SZorg on 2007-05-22
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
```


Thanks!

---

### Post by SZorg on 2007-05-22
I just discovered that if I type in:

```
 firefox google.com 
```

It opens. I still, however, get the following error: 


```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```


I fixed it, temporarily, by appending "google.com" to the shortcut. *shrug*. I would quite like a more permanent solution, though.

---

### Post by aysiu on 2007-05-22
Try [this](http://ubuntuforums.org/showthread.php?p=2569511#post2569511).

---

### Post by SZorg on 2007-05-22
I'll give it a try. Thanks a bunch. :]

---

