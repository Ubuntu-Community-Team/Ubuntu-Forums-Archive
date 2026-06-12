---
title: "CRT Help (iMac) -Can't change resolution-"
date: 2007-06-14
forum: General Help
---

### Post by Feba on 2007-06-14
I'm not sure if this is a CRT problem or an iMac problem or a video card problem, but I've added other resolutions and refresh rates in xorg, but when I switch them on Display Preferences, the screen just goes black. Anyone have an idea what could be causing this?

EDIT: Oh, I forgot to mention, this is in Xubuntu.

---

### Post by Feba on 2007-06-14
nevermind, I just need to get used to Xfce.

---

### Post by RedSquirrel on 2007-06-14
When I used Xubuntu, I just left the Display Settings on "Default" and made changes to xorg.conf. In my experience, that picks up the default resolution from xorg.conf.

I never bothered with the other resolutions listed under Display Settings.

As long as your xorg.conf is setup correctly, the "Default" setting should work fine.

Here is a guide that might help you to ensure that xorg.conf is in good shape:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

You can also post your xorg.conf file if you like.


EDIT: Obviously, you also have to have the appropriate driver for your video hardware. :)

---

### Post by Feba on 2007-06-15
I don't see a section in xorg for "default"...

---

### Post by tanelt on 2007-06-15
> **Feba said:**
> I'm not sure if this is a CRT problem or an iMac problem or a video card problem, but I've added other resolutions and refresh rates in xorg, but when I switch them on Display Preferences, the screen just goes black. Anyone have an idea what could be causing this?

CRTs are not actually supported. In my entire Linux usage history I've used DOZENS of different CRTs and even after heavy xorg.conf editing, I've only managed to get a few resolutions working properly at correct refresh rates using complex modelines.

There are rumors the next version of Xorg will fix some issues regarding it, but since it's taken them YEARS to do that, I wouldn't count on it.

Moral of the story is that the developers show the middle finger for CRT users and go back working on Beryl and other stuff.

---

### Post by Feba on 2007-06-15
I figured it out, xfce was just acting weird. It's fine now.

---

