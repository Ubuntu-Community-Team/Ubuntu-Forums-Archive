---
title: "Clean Desktop"
date: 2008-05-24
forum: General Help
---

### Post by Parvo on 2008-05-24
I don't like to have anything on my desktop; no icons, folders, nothing. Its just how I like things. 

The question is: Is there a way for my mounted drive to appear on a panel or dock and not on the desktop?

I'm using one panel and the AWN dock. Any help would be nice. 

Thanks in advance.

---

### Post by angry_johnnie on 2008-05-24
To remove icons from the desktop:

Alt + F2

```
gconf-editor
```

look for **Apps > Nautilus > Desktop**

Uncheck the boxes.

To add disk mounter applet to panel:

I'm not using GNOME right now, but I'm pretty sure there was an applet called just that, and it did exactly what you want.  :-)

right-click on panel

select **add to panel**

look for **disk mounter**.

---

### Post by geo909 on 2008-05-24
Btw, check out some different window managers outhere, like fluxbox and openbox. They are very clean and light and they don't support natively icons on the desktop. You need some time to configure them, though..

---

### Post by Parvo on 2008-05-29
> **angry_johnnie said:**
> To remove icons from the desktop:

Alt + F2

```
gconf-editor
```

look for **Apps > Nautilus > Desktop**

Uncheck the boxes.

To add disk mounter applet to panel:

I'm not using GNOME right now, but I'm pretty sure there was an applet called just that, and it did exactly what you want.  :-)

right-click on panel

select **add to panel**

look for **disk mounter**.

Thank you, that worked perfectly.

---

### Post by Parvo on 2008-05-29
> **geo909 said:**
> Btw, check out some different window managers outhere, like fluxbox and openbox. They are very clean and light and they don't support natively icons on the desktop. You need some time to configure them, though..

This is next on my list of things to tinker with, thank you. Unrelated: Will Greece be able to do it again in Euro 2008?

---

### Post by denham2010 on 2008-05-31
Try the stacks applets for awn.

There are 3 of them. The first let's you attach any folder to it, so you can use it to access your mounted volumes, ie. /home / and any others you have set up.

The second is a trash applet, no need for an explanation there.

Lastly there is the stacks plugger. It monitors hot pluggable devices like usb hard drives, media players like ipods, camera's, phones etc. When plugged in, an icon will be displayed on the awn dock, and they disappear when unmounted, just like they previously did on your desktop.

Cheers.

---

