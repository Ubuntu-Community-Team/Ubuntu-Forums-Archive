---
title: "Duel-Boot Question"
date: 2014-08-22
forum: General Help
---

### Post by chandowd on 2014-08-22
I have resently Duel-Booted my computer with Ubuntu(It already had Windows 7) and when I turn on my PC I get this screen:

[http://s936.photobucket.com/user/RavenLords/media/IMG_1320_zps9a7fed93.jpg.html?sort=3&o=0](http://s936.photobucket.com/user/RavenLords/media/IMG_1320_zps9a7fed93.jpg.html?sort=3&o=0)

But the guide says it should look like this(guide:[http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/?ALLSTEPS))

[http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/step9/Reboot-and-Configure/](http://www.instructables.com/id/How-to-Dual-boot-Linux-and-Windows-on-a-PC-with-W/step9/Reboot-and-Configure/)

Is this normal if not how can I fix this?

Thanks!
chandowd

---

### Post by grahammechanical on 2014-08-22
What you are seeing is what I see every time I boot my machine. It is what I have seen ever since I first installed Ubuntu back in 2007. We call that the Grub bootloader, (GRand Unified Bootloader). It is normal. In fact, if you look at the middle of the screen, which you do not show in your photograph, you will see that it is called Grub and you will see the version number. It will be Grub 2.2 ... I know that because you have an Advanced Options sub-menu which we did not get with Grub 1.99.

The guide that you are linking to is showing an incorrect image. It is the kind of image we see if we install Ubuntu from inside Microsoft Windows using a Ubuntu program called wubi.exe. Which, by the way is no longer supported by Ubuntu developers and cannot work on a machine with Windows 8 installed.

Can you load Ubuntu? Can you load Windows 7? So, why are you looking for something to be wrong?

Regards.

---

### Post by chandowd on 2014-08-22
Thank you!

Yes I can load Ubuntu just fine and I can also Load Windows just fine. I was just wondering whether this was normal.

Thanks again!
chandowd

---

### Post by nathanrussell-nrc02 on 2014-08-22
I think some prefer to use the Windows Boot Loader (which I think is shown on the instructables page) but so long as you can boot both OSes, GRUB is perfect.

---

### Post by ajgreeny on 2014-08-22
Just to confirm what **[COLOR=#000000][/COLOR]**[COLOR=#000000]grahammechanical**[COLOR=#000000] [/COLOR]**said[/COLOR], the picture in that guide actually shows the window of the windows boot-manager, not grub which is what you saw, as you did what the guide says and just followed the defaults.

It is just as well that there were no more slip-ups in that guide, and it shows why it is often much better to follow the guides available from this, and other ubuntu or canonical sites, rather than third party ones.

---

### Post by chandowd on 2014-08-22
Ok thank you all I understand!

---

