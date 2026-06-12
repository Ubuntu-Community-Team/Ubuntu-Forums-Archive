---
title: "On custom boot USB  how to set iptables on boot?"
date: 2018-08-18
forum: General Help
---

### Post by jhefferon on 2018-08-18
I want to make a custom Ubuntu boot.  I'm using cubic, which works great, and then the disc creator makes the USB.   I'm using 16.04.

I want to set some iptables to be put in place at bootup.  I've tried these:

1) In cubic, at the chroot prompt, I installed iptables-persistent and netfilter-persistent, and then ran ```
update-rc.d netfilter-persistent defaults
```.  The response is 
```
Running in chroot, ignoring request.
```.

2) I created a file ```
nano /etc/network/if-pre-up.d/iptablesload
``` that contains this

```
#!/bin/sh
iptables-restore < /etc/iptables.rules
exit 0
```

(where iptables.rules is the saved version of the rules) and made the file executable.  Creating a boot disc and booting had no effect.

Does the live boot disc do something different than the regular boot process?  How to hook into it?  I'd be grateful for any insight.

Jim

---

### Post by TheFu on 2018-08-18
I don't have any clue, but try specifying the full-path to any programs. Assume there is no PATH setup.

---

### Post by jhefferon on 2018-08-18
Thank you, a good thought.  But putting inthe full path did not change the behavior.

---

