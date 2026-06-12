---
title: "Fatal X-server error: Nvidia load failure"
date: 2007-01-21
forum: General Help
---

### Post by PaulFXH on 2007-01-21
Hi
I use a dual boot system (Ubuntu 6.10, WinXP) on a Dell Dimension 4550.
I just returned to this computer after a 4-month hiatus and installed Edgy (upgrade from Dapper).
Everything worked fine for about a week until this morning. When I booted the computer today (default boot option is Ubuntu), it said that Ubuntu has been mounted 30 times without a check and it went ahead and carried out the check.
Then it asked (in a non-GUI page) if I wanted to check "something" (I forget what) in the Xserver set-up to which I answered No. It then proceeded to provide a detailed Xserver output which concluded by saying "Failed to load module "nvidia" (module does not exist 0). No drivers available".
There was also some other stuff about "Wacom diver level: 47-0.7.2$ No divers available. Fatal server error: no screens available".

OK, it looks like I have a problem with my Nvidia card drivers (I have a Nvidia GeForce4 MX 420 card) and it is my intention to use this guide ([http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)) to rectify matters.

However, I would be interested to hear if this is the right move or is there anything else I need to look at. In particular, what caused the driver to fail (if that is what happened) and what do I need to do to prevent it happening again?

Thanks

---

### Post by kuja on 2007-01-21
That's likely the right move. Alberto Milone is good.

---

### Post by PaulFXH on 2007-01-22
Yes, it was the right move and worked without any problems.

---

