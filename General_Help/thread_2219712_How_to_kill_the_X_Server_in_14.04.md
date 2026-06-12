---
title: "How to kill the X Server in 14.04?"
date: 2014-04-25
forum: General Help
---

### Post by 3rdalbum on 2014-04-25
I notice the Alt-Printscreen-K combination for killing X in an emergency doesn't work in 14.04 - I get this message on the terminal/dmesg:

```
SysRq : This sysrq operation is disabled.
```

The other SysRq/Printscreen ones still work fine (you know, B to reboot, U to unmount etc).

How do you kill the X server in 14.04?

EDIT: Never mind, I found it: [http://ubuntuforums.org/showthread.php?t=2065693&p=12277030#post12277030](http://ubuntuforums.org/showthread.php?t=2065693&p=12277030#post12277030)

---

### Post by iris-n on 2014-06-15
I think [this method]("http://askubuntu.com/a/446509/293882") is much simpler. In short, run ```
sudo dpkg-reconfigure keyboard-configuration
``` and say yes when it asks you whether you want Control+Alt+Backspace to kill X.

EDIT: Sorry, I see you wanted a different shortcut. Is there any difference between Alt-Printscreen-K and Control+Alt+Backspace?

---

