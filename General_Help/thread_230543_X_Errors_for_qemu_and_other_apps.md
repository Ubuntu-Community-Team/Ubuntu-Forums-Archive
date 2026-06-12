---
title: "X Errors for qemu and other apps"
date: 2006-08-06
forum: General Help
---

### Post by glenndavy on 2006-08-06
I get this error when I try and run qemu or rdesktop:

```
$ qemu -hda ./win2k.img
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  78 (X_CreateColormap)
  Value in failed request:  0x3000001
  Serial number of failed request:  60
  Current serial number in output stream:  65
```

Im using xorg with nvdia drivers

any idea where I need to start looking to try and fix this?

thx

---

### Post by tonyric on 2006-11-01
I am experiencing the same problem here.

---

### Post by Rich_Peace on 2006-11-12
By referring to this [post]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232/comments/34")
I tried and it works for me by doing the setting below:

XLIB_SKIP_ARGB_VISUALS set to true:

XLIB_SKIP_ARGB_VISUALS=1 gnome-terminal

---

### Post by lorimer on 2006-12-22
This works great for me to get rdesktop working.  Is there a way I can make it persistent so I don't have to run it every time?  I tried /etc/profile, but no go there.  Is there a comparable file read for all X sessions (I am using KDE)?

---

