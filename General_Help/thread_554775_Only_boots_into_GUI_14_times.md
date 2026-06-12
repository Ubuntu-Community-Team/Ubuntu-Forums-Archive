---
title: "Only boots into GUI 1/4 times"
date: 2007-09-19
forum: General Help
---

### Post by Warpedflash on 2007-09-19
my problem appears to be very similar to the one listed [here]("https://launchpad.net/ubuntu/+source/xserver-xorg-driver-savage/+bug/33617") and there are a couple of workarounds listed... but i am not great with linux even though i have used it for about 2 years i have had no problems... this T21 is killing me ... lol

```
so it is definitely related to DRI. (disabling DRI resolve the problem)
I found some further information on thinkwiki.org (www.thinkwiki.org/wiki/S3_Savage_IX8)

   Option "BusType" "PCI"
   Option "DmaMode" "None"
in xorg.conf also resolve the issue but DRI is still disabled

hopefully you may further investigate the bug with this information
```

is suggested as a work around but i have no idea how to do either one... so can anybody tell me if there has been a proper fix or if not how i can do one of these work arounds.
thanks, Warpedflash

---

### Post by Warpedflash on 2007-09-19
Please help!

---

### Post by rsambuca on 2007-09-19
The link doesn't work, so it is pretty hard to help you since you didn't describe your problem in the post.  Also, bumping your thread after less than an hour isn't really good etiquette!

Now tell us what your problem is, fix the link, and maybe we can help you out!

---

### Post by Warpedflash on 2007-09-19
Sorry for bumping...
i fixed the link. The problem is described fully in that link, basically i can only boot into ubuntu 1/4 times the other 3 it just goes to a black screen. The section in the "code" box is the bit i want to try.... or think i do lol but i have no idea how to do either

---

### Post by rsambuca on 2007-09-19
Open a terminal from the top menu bar.  "Applications -> Accessories -> Terminal"

In the terminal, enter the following command to open the text editor (called gedit):
```
gksudo gedit /etc/X11/xorg.conf
```

After entering your password, the text editor will display your xorg.conf file.  In the section called "Device", enter the following line prior to the EndSection line:

```
Option "BusType" "PCI"
```Then save the file and reboot to see if that works.

---

### Post by Warpedflash on 2007-09-19
Thanks! That worked great!

---

