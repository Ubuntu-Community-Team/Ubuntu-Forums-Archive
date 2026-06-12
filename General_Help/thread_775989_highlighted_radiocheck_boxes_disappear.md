---
title: "highlighted radio/check boxes disappear"
date: 2008-04-30
forum: General Help
---

### Post by GhodMode on 2008-04-30
I've been experiencing a problem where the selected radio button or checkbox in applications disappear.  When it's a radio button, it's not too much of a problem, but on checkboxes it prevents me from determining which box is actually checked.

**[color=navy]Is anyone experiencing a similar problem?[/color]**

This isn't happening with all applications, but I haven't been able to narrow it down to a particular type of application.

The problem occurs within web sites, but not in Firefox's own dialogs.  This also occurs withing the CompizConfig Settings Manager.  I have been able to reproduce the problem under kwin.

_More Information_:

[list]
[*]Kubuntu 8.04 (Hardy Heron)
[*]Video: nVidia GeForce 6200```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

$ dmesg | grep -i nvidia
[   56.714594] nvidia: module license 'NVIDIA' taints kernel.
[   59.255946] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
```
[/list]

Thank you.

--
-- Ghodmode

---

### Post by GhodMode on 2008-04-30
I have stumbled across the solution accidentally.  It was related to the theme that KDE was applying for GTK applications.  I just installed another GTK application and, when I used it for the first time, it reported:
> The theme engine you are using, Qt, is incompatible with some of the features used by modern skins.  The incompatible features have been disabled for this session.

So, I changed the GTK theme (System Settings -> Appearance -> GTK Styles and Fonts) used to something else and the problem went away.

--
-- Ghodmode

---

