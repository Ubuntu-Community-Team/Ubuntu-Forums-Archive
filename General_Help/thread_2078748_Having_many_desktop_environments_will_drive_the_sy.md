---
title: "Having many desktop environments will drive the system crazy?"
date: 2012-10-31
forum: General Help
---

### Post by COMECON on 2012-10-31
Hi all,
I'd like to check and try all the *buntu flavours, installing their respective metapackages (I think they're) like **xubuntu-desktop**. But, as those packages install also some additional applications (e.g. gmusicbrowser with **xubuntu-desktop**), will the system become crazy? I mean, if xubuntu installs me Thunar and Kubuntu installs Dolphin, then if I want to use Unity it'll have 3 file browsers... Is there any way to fix it (e.g, that Thunar appears only on an XFCE session)?
Thanks!

---

### Post by Isamu715 on 2012-10-31
It shouldn't. Your splash screen may get changed but the system will certainly not go crazy.  Even if several applications of the same kind will be installed, ex. file managers, Nautilus will still be the default in Unity, Dolphin in KDE, Thunar in Xfce, etc. They handle their settings separately for the most part. I would recommend care with LXDE and KDE GTK settings though, as they modify some cross-environment configuration.  Also, you can always uninstall the Desktop Environments later.

If you want some applications to appear only in selected DEs you can do it by modifying their desktop entries. To do this make a copy of the desired desktop entry(copy the appropriate .desktop file from /usr/share/applications to ~/.local/share/applications) and modify/add the following line:
```
OnlyShowIn=GNOME;Unity;KDE;Xfce;
```Leave only the desired desktop environments. If you want an app to appear only in Xfce it would look like this:
```
OnlyShowIn=Xfce;
```

---

