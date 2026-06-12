---
title: "How to Open Terminal Window?"
date: 2007-11-07
forum: General Help
---

### Post by Tsu Doh Nymh on 2007-11-07
Running Xubuntu 7.10 on X86. Fresh install.
When I click on Applications > Accessories > Terminal  my session is terminated and I get logged out.
The same thing happens when I press Alt+F2  and type xfce4-terminal.
So how do I open a terminal window?

---

### Post by mali2297 on 2007-11-07
Have you tried **xterm**? (..or install some other terminal through Synaptic.)

---

### Post by Tsu Doh Nymh on 2007-11-08
Pressing Alt+F2 and typing xterm works.
Is this the way it's supposed to work?

---

### Post by mali2297 on 2007-11-08
> **Tsu Doh Nymh said:**
> Pressing Alt+F2 and typing xterm works.
Is this the way it's supposed to work?

I don't know why xfce4-terminal doesn't work for you. It isn't a major loss though since there are several other terminals available. Personally, I use rxvt-unicode.

You can add xterm, rxvt-unicode or whatever to the menu, see the menu editor for xfce. You can also create a keyboard shortcut via keyboard settings.

---

### Post by Tsu Doh Nymh on 2007-11-09
Thanks for the reply and the tips!

Still, this is a fresh default install so I'm wondering if this typical of Xubuntu. Occasionally the the video becomes corrupted for a split second when I execute xfce4-terminal before it terminates my session so I wonder if it could be a driver problem with the on-board Intel video. If so then it seems that this could be a problem for other applications too. If this is a bug then I wonder if the devs are aware of it.

Clicking Applications > Settings > Menu Editor doesn't seem to help much. The menu editor starts all right but it only lists 4 items. None of the applications are there so I don't see how to change the menus. Is this the way it's supposed to be too? I'm starting to wonder if something went wrong with my install and I need to re-do it.

---

### Post by TheExplorer on 2007-11-09
Seems to be a problem with your video drivers. Google out the workaround. There should be a fix for that. As far as I know onboard Intel is a 'funny' thing...

---

### Post by mali2297 on 2007-11-09
> **Tsu Doh Nymh said:**
> 
Still, this is a fresh default install so I'm wondering if this typical of Xubuntu. Occasionally the the video becomes corrupted for a split second when I execute xfce4-terminal before it terminates my session so I wonder if it could be a driver problem with the on-board Intel video. If so then it seems that this could be a problem for other applications too. If this is a bug then I wonder if the devs are aware of it.


I searched Launchpad and found this bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/91849)

The link gives you several tips on how to fix the problem. They involve editing the file **/etc/X11/xorg.conf**. Before you do that, make a backup of the file:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
If you manage to fix the problem, report back the solution here.

> 
Clicking Applications > Settings > Menu Editor doesn't seem to help much. The menu editor starts all right but it only lists 4 items. None of the applications are there so I don't see how to change the menus. 

To add an entry, create first a new menu. The new menu will be the same as the default but you can now add and remove entries. If you remove the entry called *system* (or something), you will lose the automatically generated menu entries. Personally, I have chosen to remove that anyhow and make my menu from scratch.

EDIT: Also, don't forget to save the menu.

---

### Post by Tsu Doh Nymh on 2007-11-11
The thread on launchpad suggested disabling both GL accelerated effects on the desktop (AIGLX) and the 'composite' extension. I found that I only needed to disable the composite extension by adding 
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
``` to xorg.conf.

Apparently this bug was reported by several people before the current release. The dev it was assigned to reported that it did not occur on his system, could not be fixed, and that he was removing it as a valid bug. Hopefully a different dev will take a look at it.

Thanks for your help.

---

