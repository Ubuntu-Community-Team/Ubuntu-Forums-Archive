---
title: "Help with compiz on laptop?"
date: 2008-06-16
forum: General Help
---

### Post by Flash786 on 2008-06-16
Hey ubuntu forum dwellers,
I've recently attempted to enable the desktop effects and i got an error saying they could not be enabled. Then I ran compiz check and it said the following:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 
```
I don't quite understand what that means though. Is there another driver I need to install, if so, how would I go about doing that?

Also, I don't know if its related, but I uninstalled compiz after I found that it wouldnt work in making cairo dock..not have lack rectangles around it. And now my ubuntu theme doesnt change, its always a dark blue.

---

### Post by collinp on 2008-06-16
This thread may help you, the people on there have similar problems and graphics chipsets: [http://ubuntuforums.org/showthread.php?t=759529](http://ubuntuforums.org/showthread.php?t=759529)

---

### Post by Forlong on 2008-06-16
You should have followed the prompt afterwards.

Run Compiz-Check again, it should ask you if you'd like to know more.

---

### Post by Rocket2DMn on 2008-06-17
Here is a guide that should help you enable compiz on your card (which uses the open source "ati" drivers) - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
Because your card is so old, you may not get very good performance out of compiz, some others with the 7500 have complained about slow performance with desktop effects.

---

