---
title: "Update messed up video"
date: 2014-04-25
forum: General Help
---

### Post by John Jason Jordan on 2014-04-25
I installed Xubuntu 13.10 on a brand new laptop with an nVidia GTX765 last December. The installation automatically installed the nouveau driver, which was fine with me, as it worked perfectly. There were some recent updates and now I have:

xserver-xorg-video-nouveau, version 1:1.0.9-2ubuntu1
libdrm-nouveau2, version 2.4.46-1ubuntu1

As a result text in windows is not refreshing in some programs (notably Claws Mail and LibreOffice. The text appears fine when I first open the program window, but as soon as I type or click some of the text disappears. If I minimize and then restore the window the text reappears properly, that is, until I type or click again.

Note that these were just updates; I have not upgraded to 14.04 (and I cannot do so, for other reasons). 

Does anyone know of a way to fix this problem? Has anyone else experienced this? Can I downgrade to the older nouveau driver?

---

### Post by John Jason Jordan on 2014-04-26
Someone please help. I need Libreoffice for my homework, and it is really hard to yuse when I can't see the menus.

---

### Post by QIII on 2014-04-26
Please wait 24 hours before bumping threads.

This is a world-wide community of volunteers from all time zones who come here as they have time.  The person with just the right answer for you may not be available right now.

Thanks.

---

### Post by monkeybrain20122 on 2014-04-26
I don't think you can downgrade, but you can upgrade the driver. It may solve your problem but may also make it worse (so do it at your own risk)
[https://code.launchpad.net/~oibaf/+archive/graphics-drivers](https://code.launchpad.net/~oibaf/+archive/graphics-drivers)
(upgrade everything it tells you to, not just nouveau, have ppa-purge installed if you do this in case something goes wrong, also disable the ppa after upgrade)

You can also try the Nvidia proprietary driver.

---

