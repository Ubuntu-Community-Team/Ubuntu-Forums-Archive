---
title: "startup commands (xmodmap)"
date: 2006-12-23
forum: General Help
---

### Post by Anonii on 2006-12-23
Greetings there!
I want 3 commands to get executed in every restart. So far my attempts are:
```
**$ cat ~/.xsession**
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "add mod4 = Super_L"
xmodmap -e "keycode 22 = BackSpace Delete"
```

```
**$ cat /etc/rc.local**
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
xmodmap -e "keycode 115 = Super_L"
xmodmap -e "add mod4 = Super_L"
xmodmap -e "keycode 22 = BackSpace Delete"
exit 0
```

I also added the commands using ```
sudo contrab -e
``` and in **System -> Preferences -> Sessions**.

What have I done wrong? The commands are not executed :/

---

### Post by tweedledee on 2006-12-23
> **Anonii said:**
> What have I done wrong? The commands are not executed :/

I'm not sure where you want wrong, but a simpler solution is to just create ~/.xmodmaprc, and put your 3 xmodmap commands there.  Each time you log in, your xmodmap commands should be executed.

---

