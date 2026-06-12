---
title: "ctrl-alt-del"
date: 2007-09-25
forum: General Help
---

### Post by perce on 2007-09-25
In the good old days when I was using Debian ctrl-alt-del rebooted the computer, now it looks disabled in Ubuntu. How can I repristinate it to its true and original function?

Thanks a lot

---

### Post by mcduck on 2007-09-25
Press Alt-SysRq-R (SysRq is in the same key with PrtScr) and the Ctrl-Alt-Del. But I wouldn't recommend doing that unless the system is frozen and it's the only option besides pushing the power button..

---

### Post by perce on 2007-09-25
The point is that ctrl-alt-del is supposed to reboot in a "nice" way, not like alt-SysRq-b (if this is what you are talking about)

---

### Post by pointone on 2007-09-26
Please post the contents of the following file on your system:

/etc/event.d/control-alt-delete

---

### Post by perce on 2007-09-28
> **pointone said:**
> Please post the contents of the following file on your system:

/etc/event.d/control-alt-delete

# control-alt-delete - emergency keypress handling
#
# This task is run whenever the Control-Alt-Delete key combination is
# pressed.  Usually used to shut down the machine.

start on control-alt-delete

exec /sbin/shutdown -r now "Control-Alt-Delete pressed"

---

### Post by mcduck on 2007-09-28
> **perce said:**
> The point is that ctrl-alt-del is supposed to reboot in a "nice" way, not like alt-SysRq-b (if this is what you are talking about)

If you didn't read my full message, it says to press **Alt-SysRq-R** and then **Ctrl-Alt-Del**, not Alt-SysRq-B. ;)

So what I told to do actually does a "nice" reboot.

---

### Post by perce on 2007-09-28
> **mcduck said:**
> If you didn't read my full message, it says to press **Alt-SysRq-R** and then **Ctrl-Alt-Del**, not Alt-SysRq-B. ;)


Sorry :oops:

---

