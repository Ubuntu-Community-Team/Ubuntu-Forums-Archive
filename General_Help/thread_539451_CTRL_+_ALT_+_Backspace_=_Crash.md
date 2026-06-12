---
title: "CTRL + ALT + Backspace = Crash"
date: 2007-08-31
forum: General Help
---

### Post by 5h4rk on 2007-08-31
Hi,

everytime I hit the key stroke, it crashes and i have to power off and power on again manually...

I'm running CF.

What could be the possible problem?

Thanks.
[B]
EDIT:[/B]

Ok, it's not only CTRL + ALT + Backspace, and I think the problem may be in CF, cuz when i try to change from Compiz to Metacity, it crashed as well, well, im not sure it did crash or not, i could move my mouse and thats all, all windows frozen and the keyboard dead. And the funny thing is when after i restarted, CF is using metacity instead of compiz...

:S

I'm running CF and CF Icon, and I set CF Icon to start automatically in session.

Thanks.

---

### Post by mckryptyk on 2007-08-31
When you hit Ctrl + Alt + Backspace, You are telling Xorg to restart it's service.

Xorg is the service that controls the graphical part of your linux system.

Don't worry, It's just doing what you tell it to, what it is supposed to do. :)

As for the switching causing crashes, you may have xorg.conf set up incorrectly or you may not be using the non-free drivers for you graphics card.

Please search the forum for any compiz related issues you might have.

Cheers.

---

