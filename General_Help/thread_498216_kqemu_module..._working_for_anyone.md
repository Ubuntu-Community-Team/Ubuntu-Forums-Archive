---
title: "kqemu module... working for anyone?"
date: 2007-07-11
forum: General Help
---

### Post by buebo on 2007-07-11
Hi,
I'm having some trouble installing the kqemu module synaptic source.

This is what I have done so far:

```

sudo apt-get install kqemu-source kqemu-common

compile and install it with 'module-assistant'

sudo modprobe kqemu

```

No errors, but there's no kqemu device node. What am I missing here?

Cheers

---

### Post by mocha on 2007-07-12
Good freaking question.  I still haven't figured it out.

---

### Post by Eddi3 on 2007-07-23
I followed this HowTo:

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

Althought the guide focuses on getting Windows to work, it also covers how to get kqemu working in detail.

---

### Post by lathanial on 2007-08-30
Same as buebo. There seems to be some steps missing from the "WindowsXPUnderQemuHowTo".  I've followed the steps outlined, received no errors but when I get to step 7 there is no /dev/kqemu. The HowTo says it was last edited 2007-08-19 13:27:03 by Yoyovicks. I would ask her/him but I can't find a contact. Speaking for myself, the HowTo may be fine and I just don't have the smarts to do a couple of steps it is assumed I know about. I sure would appreciate some one replying with the solution - that is - if you are out there. Somewhere ;)

Thanks
Lathanial

---

### Post by joebaker on 2007-09-15
This command should be run before modprobe kqemu....
[INDENT]sudo update-modules[/INDENT]

Then
[INDENT]modprobe kqemu[/INDENT]

And now
[INDENT]ls -la /dev/kqemu[/INDENT]
should yeild the desired results needed for udev.

---

### Post by lathanial on 2007-09-18
Thanks for the post but I'm still having the same problem with kqemu. I've followed the rest of the instructions and I have XP running but it would be nice to speed it up some. When I run 
      modprobe kqemu 
it makes an entry in modules.dep but that is the only evidence I can find that anything happens. There is no /dev/kqemu.

Any other ideas?

Thanks,
Lathanial

---

