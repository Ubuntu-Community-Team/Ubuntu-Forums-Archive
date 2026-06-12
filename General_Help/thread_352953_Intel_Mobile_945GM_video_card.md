---
title: "Intel Mobile 945GM video card"
date: 2007-02-04
forum: General Help
---

### Post by Fire on 2007-02-04
I am using the mobile intel 945gm video card and can not get the resolution I would like.  Infact only one is listed - 1440x900 I want to use 1920x1440.  When I run 915resolution it actually shows me everything and 1920x1440 is listed.  I am not sure how to handle this.. I even tried to change everything using 915resolution that says 1440x900 to say 1920x1440 just to see if anything would change but it does not..

any help would be great.

Thank you

---

### Post by ZERO_SHIFT on 2007-02-04
Are you sure your graphic card supports that resolution?

---

### Post by Mba7eth on 2007-02-04
Well i had the same problem with my Dell laptop inspiron 640m. It also has the intel 945gm video card. Check this [HACK ]("http://www.ubuntuforums.org/showthread.php?t=347066"). 
But you'll notice a very slow bootup process that I really don't WHY??? 
I ask the Question and no one answered. I really don't know :mad: I'm still a newbie

---

### Post by Fire on 2007-02-04
Yes I am sure that it supports it as that is the resolution.

This is from the Intel Website.
Offering high performance multi-threaded parallel computing, low power, sufficient I/O bandwidth  
for PCIe, SCSI, and 2D/3D graphics performance with up to [COLOR="Red"]2048 x 1536 resolution[/COLOR], a wide range of applications stand to benefit.

Mba7eth it looks like I would have to reload my system to do it your way... I was hoping there would be a way to get this to work with out doing all that..

thank you for your help...

Ill keep it in mind.

---

### Post by Mba7eth on 2007-02-04
here is a hint ! 
use any other virtual terminal ( Gtrl+Alt+F2 for example ) to get back to the xwindow Ctrl+Alt+F7.
from there type login as usual the followings : 
```

$sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_my_back_up
$sudo /etc/X11/gdm stop

```
now your xserver is stoped .... just give it a try and if you are not satisfied you can get ur old configuration by copying the backup to its origin :) 
```

$sudo cp /etc/X11/xorg.conf_my_back_up /etc/X11/xorg.conf
$startx
```  
That's all 
I hope i am clear and helpful  ):P

---

### Post by m_janos on 2007-02-10
I'm not an expert but I think that though the card can do the higher resolution the screen can't. I think allowable resolutions come from an intersection of the xorg.conf file the graphics driver and the monitor.

Michael

---

