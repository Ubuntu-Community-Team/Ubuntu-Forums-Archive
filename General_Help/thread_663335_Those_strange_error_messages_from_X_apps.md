---
title: "Those strange error messages from X apps"
date: 2008-01-10
forum: General Help
---

### Post by yurimxpxman on 2008-01-10
I've never seen a GNU/Linux system that doesn't do this, so I know it's normal, but what exactly does this mean, and why is it there? Whenever I run an X application, it sends this to the stdout:

```
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Is there any way to stop this?

---

### Post by zionpsyfer on 2008-01-10
I believe that the wacom entry in your xorg.conf file is causing that.  Try deleting the entry out of it and restarting X.

---

### Post by yurimxpxman on 2008-01-10
You're right. Thanks! :D

---

### Post by jlacroix on 2008-01-10
Makes me wonder why they just don't permanently kill that entry in new installs.

---

### Post by yurimxpxman on 2008-01-10
> **jlacroix said:**
> Makes me wonder why they just don't permanently kill that entry in new installs.

I agree. I think it's silly they assume everyone has a tablet PC. They could at least check for it.

---

### Post by yurimxpxman on 2008-01-10
I just submitted it as a bug ([181914](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/181914))

---

### Post by sumguy231 on 2008-01-10
Are you still using Feisty? As far as I can tell, the Wacom tablets are disabled by default in xorg.conf in Gutsy.

---

