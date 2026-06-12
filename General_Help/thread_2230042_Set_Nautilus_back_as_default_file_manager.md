---
title: "Set Nautilus back as default file manager"
date: 2014-06-16
forum: General Help
---

### Post by Brandon_MacEachern on 2014-06-16
Ok so at one point I set Caja as my default file manager when I was using MATE.  However I couldn't get MATE to work for me the way I wanted it to, and removed it, including Caja.  However, apparently when plugging in my Android phone, Caja still automatically pops up, which is very strange, considering it's not supposedly installed.  I can not get Nautilus to seemingly be the default.  Is there any way to just kill this association with Caja (or a ghost of it since it's not actually installed according to Synaptic Package Manager, but somehow manages to launch).

---

### Post by grumblebum2 on 2014-06-16
Terminal..
```
xdg-mime default nautilus.desktop inode/directory application/x-gnome-saved-search
```
Don't know if caja draws the desktop but may also want to run...
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by Brandon_MacEachern on 2014-06-17
Thanks I'll try this in the morning and see how it works.  Hopefully it does.

It's still weird that Caja can even open up when it's technically gone.

---

### Post by grumblebum2 on 2014-06-17
> **Brandon_MacEachern said:**
> Thanks I'll try this in the morning and see how it works.  Hopefully it does.

It's still weird that Caja can even open up when it's technically gone.
If caja does draw the desktop and was running in the background(as nautilus does) to do this
I think it may continue to run until you reboot or killall caja.

As caja is a fork of nautilus I assume it would behave this way.

---

