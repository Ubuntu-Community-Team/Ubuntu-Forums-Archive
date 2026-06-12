---
title: "Can't delete defective shortcut from desktop"
date: 2017-08-09
forum: General Help
---

### Post by steve169 on 2017-08-09
I'm running Lubuntu 16.04 from a thumb drive on a Dell desktop computer.

A mysterious shortcut has appeared on my desktop; I have no idea where it came from.

I have tried every way I can to delete the shortcut, but I always get an error message saying the file does not exist.

The offending shortcut is labeled "0000" in the screen shot below. The "File Properties" window refers to the shortcut.

[ATTACH=CONFIG]276336[/ATTACH]

How can I get rid of it?

---

### Post by papibe on 2017-08-09
Hi steve169,

Try this from the terminal:
```
rm ~/Deskop/0000
```
Let us know how it goes.
Regards.

---

### Post by steve169 on 2017-08-09
Thank you, papibe, for your quick reply.

But the problem solved itself. As soon as I closed down Lubuntu, then rebooted, the phantom shortcut was gone.

I feel like an idiot, but an idiot with one fewer problem.

Many thanks.

---

