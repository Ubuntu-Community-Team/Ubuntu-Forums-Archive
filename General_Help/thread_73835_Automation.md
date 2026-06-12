---
title: "Automation"
date: 2005-10-10
forum: General Help
---

### Post by shandar on 2005-10-10
Hi!

I have about 100 photos that I need to resize and rename which I really dont want to do by hand... What is the best way of doing this? Is it to write some kind of script or is there an app (like the OSX Automator) that can help me do it?

Cheers!

---

### Post by heimo on 2005-10-10
Oh! Great question! There's a library / collection of tools called ImageMagick - and it's a magical, incredible piece of software. It can do amazing stuff - it knows somehere around 70 different image formats, it resizes, converts, runs unsharpen masks... And if you know a little bit bash scripting, you can forget GUI stuff like Gimp - and never watch your photograps while editing. ;)
[http://packages.ubuntu.com/hoary/graphics/imagemagick]("http://packages.ubuntu.com/hoary/graphics/imagemagick")
[http://www.imagemagick.com/]("http://www.imagemagick.com/")

(use convert with resize flag) - if you need specific instructions, just ask and some bash wizard will probably post answers (or me, if bash gurus are sleeping)

EDIT: links:
[http://www-128.ibm.com/developerworks/linux/library/l-graf/?ca=dgr-lnxw02ImageMagick](http://www-128.ibm.com/developerworks/linux/library/l-graf/?ca=dgr-lnxw02ImageMagick)
[http://www.linuxdevcenter.com/pub/a/linux/2000/07/11/LivingLinux.html](http://www.linuxdevcenter.com/pub/a/linux/2000/07/11/LivingLinux.html)

---

