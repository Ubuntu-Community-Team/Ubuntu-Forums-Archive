---
title: "After installing Ubuntu on a new SSD, the old SSD boots the new one."
date: 2015-04-24
forum: General Help
---

### Post by _sluimers_ on 2015-04-24
Something went wrong during the installation I think, because when I try to boot my old SSD, it boots the other.
When I try booting the new one I get a black screen with only a blinking underscore.
When I try booting the old one without the new one, it can't find the device.

---

### Post by ajgreeny on 2015-04-24
See Boot-Repair in my signature and follow the instructions to run it but just to get the report and post back here with the pastebin link you are given; don't at this stage accept the default repair.

---

### Post by _sluimers_ on 2015-04-27
[http://paste.ubuntu.com/10912467/](http://paste.ubuntu.com/10912467/)

---

### Post by _sluimers_ on 2015-04-27
[http://paste.ubuntu.com/10912467/](http://paste.ubuntu.com/10912467/)

I no longer get just a blinking underscore, now it's something like: 

```
device not found: 901642-ab8742f-986afg
grub rescue >
```


[UPDATE]

I have managed to reinstall grub and it's now able to find the device. However it's still all in terminal, rather than a normal menu.
So now I get:
grub >

Can I now get in with a command?

---

### Post by _sluimers_ on 2015-04-29
Since the problem has changed (it now ends up in intramfs), I will mark this one as solved and open a new thread.

---

