---
title: "tesco internet phone e337 prob"
date: 2007-12-12
forum: General Help
---

### Post by bhuthogg on 2007-12-12
Hi,

I have purchased and successfully got a tesco internet phone up and running via  KIAX
But i am having a little problem getting Ubuntu to use the devices mic i can make and recieve calls but cannot hear anything when i speak into the tesco phone :( 

Seen here is setup i have on kiax [[img]http://img2.freeimagehosting.net/uploads/th.c7dbcc243d.jpg[/img]](http://img2.freeimagehosting.net/image.php?c7dbcc243d.jpg)

and here is setup on tesco internet phone in WINE i didn't really think this was gonna work but it did as exactly KIAX did [[img]http://img2.freeimagehosting.net/uploads/th.078614c3ee.jpg[/img]](http://img2.freeimagehosting.net/image.php?078614c3ee.jpg)

what is interesting is i can hear myself on the device so the microphone is working just not quite configured correctly to be used in ubuntu by the look of things  here is one of sound in system/preferences  [[img]http://img2.freeimagehosting.net/uploads/th.b7d2ded1a7.jpg[/img]](http://img2.freeimagehosting.net/image.php?b7d2ded1a7.jpg)

hope someone can help me :) please

Thanks for reading if not

---

### Post by bhuthogg on 2007-12-12
bump

---

### Post by bhuthogg on 2007-12-13
bump2

---

### Post by adonicus on 2007-12-13
[FONT="Courier New"][SIZE="4"]This may seem like an obvious question, but have you adjusted the microphone sound volume using a mixer control application like alsamixer(1) or the Gnome volume control app?

Also, you need to change "Sound capture" in the sound control panel from "Test Sound" to "Alsa" or a specific hardware device.

Cheers,

Paul[/SIZE][/FONT]

---

