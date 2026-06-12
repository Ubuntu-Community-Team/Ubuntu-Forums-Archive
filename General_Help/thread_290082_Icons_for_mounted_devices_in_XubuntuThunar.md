---
title: "Icons for mounted devices in Xubuntu/Thunar"
date: 2006-10-31
forum: General Help
---

### Post by rrwo on 2006-10-31
When I'm in Gnome/, mounted volumes are shown in the file manager (Nautilus).

But when I'm in Xfce--which I prefer, mounted volumes are not shown in the file manager (Thunar).  I can still access them via their mount points, but it would be nicer to have the shortcuts to them in the top level.

---

### Post by kerry_s on 2006-10-31
Just create a short cut, grab the media folder and drag it under filesystem.

---

### Post by rrwo on 2006-11-01
What I'm talking about are shortcuts that are dynamically added when a device is mounted (in the top left where the filesystem icon is).

---

### Post by kerry_s on 2006-11-02
I guess your's is not doing that auto magically? When i plug a device in it creates a icon. Try installing ivman. Pic with pen drive plugged in and with out->

---

### Post by rrwo on 2006-11-03
Installing ivman doesn't have any effect.

---

### Post by danielph on 2006-12-12
In the way of a BUMP I was wondering if you got this sorted. If you install ivman you would have to run it at startup and also configure it. The user that runs it would also need to be in the group plugdev. Check out the man page and  [http://xaprb.com/blog/2006/05/20/how-to-auto-mount-removable-devices-in-gnulinux/](http://xaprb.com/blog/2006/05/20/how-to-auto-mount-removable-devices-in-gnulinux/) The only other option I know is to install gnome-volume-manager, not ideal as it drags in a huge list of dependencies. 

I believe there is a project for xfce4-volume-manager happening at the moment also and that this maybe the answer.

If you have found another solution I would be interested to know.

---

### Post by Wight_Rhino on 2006-12-15
Mine creates the Icons on plug-in, I don't have lvman. I don't know why it does it automagically, but it does.

---

### Post by danielph on 2006-12-15
I should explain the problem with my setup. Yes, I get icons on the desktop. My exact problem is configuring a laptop for a newbie (computer newbie - not just linux) and they really need to see the applications come up when they insert a DVD or plug in a camera. Xubuntu does not do this by default and I believe ivman or gnome-volume-manager are currently the only options for this.

---

### Post by Yuzem on 2007-04-28
I am using Gnome, when I insert a CD it gets mounted but it doesn't show on the thunar sidebar.
Anyone know what is the problem?

---

### Post by rrwo on 2007-05-03
This was fixed for me a while ago by upgrading Thunar to the latest version.

---

### Post by Yuzem on 2007-05-03
The cause of my problem was a previous Thunar installation.
I did:
Applications > System tools > Software Uninstaller
That did not let me remove anything and I had to do it with super powers (sudo):
```
sudo /usr/local/bin/i2t-uninstaller
```
I had two thunar installations. I remove them all and the default Feisty Thunar now works like a charm.

That fixed all my thunar problems!

---

### Post by Andreas1 on 2008-06-30
ok, can anyone tell me if this is the way it is supposed to be:
in the thunar sidebar there are icons for:

-userfolder
-trash
-desktop
-filesystem "/"
-EXTERNAL MOUNTED DRIVES (are automatically mounted, works fine)

but there are no icons for INTERNAL mounted or unmounted drives/partitions
which i would really appreciate to have, since my personal data is not on "/" but on an extra partition on my internal hardisk

---

