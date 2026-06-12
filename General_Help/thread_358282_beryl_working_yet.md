---
title: "beryl working yet?"
date: 2007-02-10
forum: General Help
---

### Post by mwolfe on 2007-02-10
has anyone got the latest version of beryl running. On feb 2nd they had an update that seems to have screwed up most peoples system. It hasnt had an update since and its been broken since then.I have an ati x600 with the fglrx drivers installed (the repository version not the latest version that you have to compile yourself)
```

mwolfe@mwolfe-desktop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

```

mwolfe@mwolfe-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Checking for non power of two texture support   : failed

```


anyone have info on this?

---

### Post by bornakke on 2007-02-11
Maybe you could try to look here. Not a solution just a work around...[http://ubuntuforums.org/showthread.php?t=352350](http://ubuntuforums.org/showthread.php?t=352350)

---

### Post by cmost on 2007-02-11
I don't mean any disrespect, but why don't you just use the last stable version of Beryl (0.1.5)?  Obviously the SVN build is in heavy development and bound to be broken at any given time.  It's not something you can really complain about; it's an unstable, developmental branch by definition.  Furthermore, "they haven't had an update since then" doesn't say much.  What you really mean to say is the maintainer of the repository from which you get your binary SVN packages hasn't built a new snapshot of the SVN since then.  You could always fetch and compile the latest Beryl SVN yourself if you insist on living on the bleeding edge.  There are numerous instructions for doing this...try Google.  If you're not comfortable building the latest and greatest on your own, and you value stability (which your post implies) then I suggest you try the Beryl Wiki, update your /etc/apt/sources.list to use a stable Beryl repository and then downgrade to the last stable version.  You'll have much better luck with that one.  I've read that the 0.2.0 stable should be out shortly.  Good luck.

---

### Post by mwolfe on 2007-02-11
i did use beryl wiki to do the install: 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

It doesnt work anymore though since that one update. If someone breaks a package they should have the decency to redistribute a working version it seems.. Whatever though i know its free, i was just wondering if anyone had found a fix besides resorting to the previous version.

---

