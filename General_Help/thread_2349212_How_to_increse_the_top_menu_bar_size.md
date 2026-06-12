---
title: "How to increse the top menu bar size?"
date: 2017-01-12
forum: General Help
---

### Post by satimis on 2017-01-12
Hi all,

How to increse the top menu bar size?

Setting -> Displays

'Scale for menu and title bar' only increases the size of the left menu bar

Thanks

Regards
satimis

---

### Post by slickymaster on 2017-01-12
See this: [How to adjust top menu bar size]("http://askubuntu.com/questions/506273/how-to-adjust-top-menu-bar-size")

---

### Post by satimis on 2017-01-12
> **slickymaster said:**
> See this: [How to adjust top menu bar size]("http://askubuntu.com/questions/506273/how-to-adjust-top-menu-bar-size")
Hi,

Thanks for your link.

I already have "unity-tweak-tool" installed.  I can increase the font size but unable to enlarge the top menu bar size.

Regard
satimis

---

### Post by slickymaster on 2017-01-12
Have you tried to change the **panel_height** property in **panel/PanelStyle.cpp**&#8203; ?

---

### Post by satimis on 2017-01-12
> **slickymaster said:**
> Have you tried to change the **panel_height** property in **panel/PanelStyle.cpp**&#8203; ?
Where can I find PanelStyle.cpp

&#10219; locate PanelStyle.cpp
no output

&#10219; sudo find / -name panel```

/usr/src/linux-headers-4.4.0-31-generic/include/config/panel
/usr/src/linux-headers-4.4.0-59-generic/include/config/panel
/usr/src/linux-headers-4.4.0-59/drivers/staging/panel
/usr/src/linux-headers-4.4.0-59/drivers/gpu/drm/panel
/usr/src/linux-headers-4.4.0-59/drivers/video/fbdev/mmp/panel
/usr/src/linux-headers-4.4.0-31/drivers/staging/panel
/usr/src/linux-headers-4.4.0-31/drivers/gpu/drm/panel
/usr/src/linux-headers-4.4.0-31/drivers/video/fbdev/mmp/panel
find: ‘/run/user/1000/gvfs’: Permission denied
/lib/modules/4.4.0-59-generic/kernel/drivers/staging/panel
/lib/modules/4.4.0-31-generic/kernel/drivers/staging/panel

```

Whether following link apples to my case?
Increase Menu Bar Size
[http://askubuntu.com/questions/342734/increase-menu-bar-size/430295](http://askubuntu.com/questions/342734/increase-menu-bar-size/430295)

I'm running Gnome desktop.  Thanks

Regards
satimis

---

### Post by howefield on 2017-01-12
Have a look at [this thread]("https://ubuntuforums.org/showthread.php?t=2272686"), (specifically deadflowrs post #10) although the thread is primarily concerned with font size it might give you some pointers to the actual panel sizing.

---

### Post by slickymaster on 2017-01-12
Can't be sure, as they were using 12.04. But you could give it a try.

---

### Post by satimis on 2017-01-12
> **howefield said:**
> Have a look at [this thread]("https://ubuntuforums.org/showthread.php?t=2272686"), (specifically deadflowrs post #10) although the thread is primarily concerned with font size it might give you some pointers to the actual panel sizing.

on deadflow #10
clicking "user themes extension from gnome extensions" it starts;

[https://extensions.gnome.org/extension/19/user-themes/](https://extensions.gnome.org/extension/19/user-themes/)

Warning: We cannot detect a running copy of GNOME on this system, so some parts of the interface may be disabled. 

What is it?  
This is a newly installed PC with Ubuntu 16.04 running on a SSD.  Installation went through without problem.  apt-get update/upgrade also has been run.

&#10219; cat ~/.xsession-errors```

openConnection: connect: No such file or directory
cannot connect to brltty at :0

```

&#10219; ls ~/.xsession-errors```

/home/satimis/.xsession-errors

```

&#10219; cat /home/satimis/.xsession-errors```

openConnection: connect: No such file or directory
cannot connect to brltty at :0

```

Edit-1:
&#10219; apt-cache policy gnome```

gnome:
  Installed: (none)
  Candidate: 1:3.14+3ubuntu1
  Version table:
     1:3.14+3ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

&#10219; sudo apt-get install gnome

Default display manager:    
gdm3
lightdm(selected)		
<Ok> 

Reboot PC.

Still I couldn't find to enlarge menu size on /panel

clicking "user themes extension from gnome extensions" - the warning is still there

&#10219; apt-cache policy gnome-shell-extensions```

gnome-shell-extensions:
  Installed: 3.18.3-2
  Candidate: 3.18.3-2
  Version table:
 *** 3.18.3-2 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status

```

gnome-shell-extensions already installed

Edit-2:
While holding [Alt] right click on top menu bar```

Minimize (greyout)
Maximize (greyout)
Move (greyout)
Resize (greyout)
Always on top (check)
close (greyout)

```

Holding [Windows] and [Alt] right click on top menu bar - no action


satimis

---

