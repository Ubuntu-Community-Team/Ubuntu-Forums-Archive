---
title: "unable to launch xfburn"
date: 2015-06-30
forum: General Help
---

### Post by rmcellig on 2015-06-30
I just installed Lubuntu 14.04. When I went to launch XFBurn from the terminal, this is what I get:

```


randy@lubuntut60:~$ xfburn
** Message: No existing settings file, using default settings
** Message: Using UDEV
Segmentation fault (core dumped)


```

How can I resolove this problem?

---

### Post by kerry_s on 2015-06-30
sudo apt-get purge xfburn
sudo apt-get install xfburn

---

### Post by tgalati4 on 2015-06-30
xfburn is designed for the XFCE4 desktop environment.  You are running Lubuntu which is based on LXDE, so you may be missing some libraries.

> tgalati4@Mint17 ~ $ apt-cache depends xfburn
xfburn
  Depends: libburn4
  Depends: libc6
  Depends: libexo-1-0
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgstreamer-plugins-base0.10-0
  Depends: libgstreamer0.10-0
  Depends: libgtk2.0-0
  Depends: libgudev-1.0-0
  Depends: libisofs6
  Depends: libxfce4ui-1-0
  Depends: libxfce4util6
  Conflicts: xfburn:i386


---

### Post by Rex Bouwense on 2015-06-30
LXDE also uses Xfburn by default.  Great program.

---

### Post by Dennis N on 2015-06-30
Try starting it through the application menu, and see if that makes a difference. In any case, you will get an error message first if there is no burner detected, then you reach the main window with all the options. Or you can insert a blank cd and a popup message will offer to open xfburn for you.

I burned an audio cd maybe 4 days ago with it on Lubuntu 14.04 and all was good. 

Xfburn is also a default application on Lubuntu.

---

### Post by Yellow Pasque on 2015-06-30
File a bug and it will automatically trace the segfault, and you may find it's already been reported and there's a workaround.

---

### Post by Dennis N on 2015-07-01
> **Rex Bouwense said:**
> LXDE also uses Xfburn by default.  Great program.

I agree, Xfburn works very well. Even so, I mostly go to Brasero because you can save your projects for later editing and reuse (adding or subtracting tracks, changing order, another copy later, etc) without re-assembling the whole list. Xfburn has no File > Save (unless there is a way to do this that I haven't found. Is there?)

---

### Post by Rex Bouwense on 2015-07-01
Coincidence.  I think not.  I have not discovered a way to save projects using Xfburn.  I too have Brasero installed on my Lubuntu.  Are you a member of the Arizona Ubuntu Local Community?

---

