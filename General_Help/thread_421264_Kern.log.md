---
title: "Kern.log"
date: 2007-04-24
forum: General Help
---

### Post by YetAnotherNoob on 2007-04-24
First time linux user be gentle.

For several days I have been using Feisty Faun 7.04 on my Dell Inpiron 9400 notebook and have been having system lockups.  It happens frequently but randomly and I cannot reproduce it at will.  Everything locks up during this mouse keyboard.  At times Caps lock and scroll lock have blinked repeatedly, but not always.  

From reading the forums I gather that Video drivers or ACPI are the "usual suspects".
I have not yet attempted to disable ACPI but will if it comes to that.  The card is an nVidia 7800 GO.

I am using the NVidia drivers downloaded automatically for me using "Restricted Drivers".
Looking in kern.log I see entries:

[FONT="Courier New"]Apr 24 23:06:52 matthew-laptop kernel: [   27.268000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[/FONT] 

Is this a problem, does it require action?

Possibly unrelated:
Memory tests pass.
This notebook has been running WinXP and vista without problems for several months.

thank you

---

### Post by YetAnotherNoob on 2007-04-25
The warnings are not the cause of the freezes:
googled:
[http://http://bbs.archlinux.org/viewtopic.php?pid=244152]("http://http://bbs.archlinux.org/viewtopic.php?pid=244152")
[http://lkml.org/lkml/2007/3/6/61]("http://lkml.org/lkml/2007/3/6/61")

The constant freezes have not stop, it stopped during typying this response!
But the nVidia driver warnings are apparently  unrelated

---

