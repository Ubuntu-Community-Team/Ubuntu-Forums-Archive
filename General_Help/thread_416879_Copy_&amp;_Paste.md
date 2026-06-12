---
title: "Copy &amp; Paste"
date: 2007-04-21
forum: General Help
---

### Post by Gorlist on 2007-04-21
Hi, right quick question when it comes to copy and paste, since using linux/ubuntu one of the problems I keep finding is you can't paste items if you have closed the area where you copied it from - e.g. if you select and copy some text from a webpage, the close the browser and try to paste into say a document your unable to do so.

What's the reason for this? and can it be cured :)

Regards!

---

### Post by ArieT on 2007-04-21
I don't know the exact reason for this but i know the program glipper will solve your problem. Install it with synaptic or
```

apt-get install glipper

```
After installing you can launch it with
```

glipper

```
or select it in the menu.

---

### Post by Gorlist on 2007-04-21
Thanks! it works, just not really an ideal solution as its something extra that needs opening.. 

Still would be interested in the reason for this? :) :confused:

---

### Post by lluisanunez on 2007-04-21
I can't install glipper in  Edgy:
```

lluisa@laptop:~$ sudo apt-get install glipper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package glipper
lluisa@laptop:~$ 

```

Edited: I see, it comes with Feisty
On Edgy I'm using gnome-clipboard-daemon, just to keep things in clipboard even when closing the window.

---

### Post by Ziggy72 on 2007-04-21
lluisanunez - Glipper won't respoond to a terminal command. Once installed It should start at each reboot and then appear as a panel icon. If the icon fails to appear, make sure it begins at startup by going to Systems > Preferences > Sessions. If you don't see glipper under the Startup Programs tab, click New and type Glipper as the name and glipper as the command.

---

### Post by lluisanunez on 2007-04-22
**Ziggy72:**
Thanks, but I can't **install** it,  it seems it comes only with Feisty. Looks good, like the clipboard manager in XFCE so I'll wait till I'm on Feisty

**Gorlist:** 
Try this script, [gnome-clipboard-daemon]("http://members.chello.nl/~h.lai/gnome-clipboard-daemon/")
Once it's running, you don't have to do anything, copy&paste just works, even if you closed the windows.

---

### Post by hikaricore on 2007-04-22
glipper is in the edgy universe repos if I'm not mistaken, i used it forever until I switeched to kde.

---

### Post by Brucevdk on 2007-04-22
**lluisanunez**: like hikaricore indicated, glipper was available in Edgy through the universe repository. [Looks like they might have moved it to backports]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=glipper&searchon=names&subword=1&version=edgy-backports&release=all"), enable backport updates to get it.

**Gorlist**: as for the reason, from [the clipboard specifications]("http://standards.freedesktop.org/clipboards-spec/clipboards-latest.txt"):

> 
A remaining somewhat odd thing about X selections is that exiting the app you did a cut/copy from removes the cut/copied data from the clipboard, since the selection protocol is asynchronous and requires the source app to provide the data at paste time. The solution here would be a standardized protocol for a "clipboard daemon" so that apps could hand off their data to a daemon when they exit. Or alternatively, you can run an application such as xclipboard which constantly "harvests" clipboard selections.


---

### Post by Gorlist on 2007-04-22
Thanks for the replies - I think it should certainly be addressed in Ubuntu, specially for a Windows user moving to Linux, its  can be very annoying when you don't think of it :)

Will try **gnome-clipboard-daemon** shortly.

Regards!

---

### Post by lluisanunez on 2007-04-22
Brucevdk,
Enabled backport updates, that did it!
Thanks,

---

### Post by Gorlist on 2007-05-01
Sorry, solved the problem just as I posted :)

---

