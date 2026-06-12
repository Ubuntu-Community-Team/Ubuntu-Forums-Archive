---
title: "run shell scripts from nautilus"
date: 2022-11-23
forum: General Help
---

### Post by bitrat2 on 2022-11-23
Hi.  

I just assumed my difficulty finding how to do this was a personal failure, but it seems such conveniences have been REMOVED from GNOME.

 And what is the minimum alternative?  Is it really necessary to install the Nautilus fork Nemo, as apparently recommended, even by GNOME developers themselves!

[https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28](https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28)

Cheers,
bitrat

---

### Post by TheFu on 2022-11-24
Gnome has been protecting noobs from themselves far too much, it seems.
And for people smart enough to seek out alternative solutions, they figure we are smart enough to live with the good and bad consequences, I suppose.   OTOH, making it a local preference in the Options/Preferences might not work for all the platforms they want to support.  

For example, suppose Nautilus runs inside a snap. By default, snaps can't access /usr/local/ where lots of people would place system-wide scripts. It would just point out flaws in the snap packaging tool, but Gnome would be blamed for it.

Generally, I want to redirect program output, so running them from a GUI isn't an option.
Does Nautilus run .desktop files?  Have you tried making a .desktop file that points at the script?  I don't know, just guessing at an option.

---

### Post by MAFoElffen on 2022-11-24
I don't specifically know about this change- about how it will affect scripts executing from directly nautilus. I one of those, let me see what it actually does.

I'm going to spin up a new Fedora instance with Gnome 3.28 and see for myself... Will post later on what it does.

---

### Post by MAFoElffen on 2022-11-24
Okay... Fedora 38 DEV:
```

mafoelffen@fedora ~]$ gnome-shell --version
GNOME Shell 43.1
[mafoelffen@fedora ~]$ nautilus --version
GNOME nautilus 43.0

```
I can still start scripts directly from Nautilus there.

EDIT: I had to check this to ensure the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") still works for Fedora Users. I made sure it was compatible with... because of a review from Distro Watch, it now has a following from Fedora and RHEL Branch Users to use as a Linux tool.

For Lunar 23.04 it still work also...
```

mafoelffen@ZFS-23:~$ gnome-shell --version
GNOME Shell 43.0
mafoelffen@ZFS-23:~$ nautilus --version
GNOME nautilus 43.0

```

---

### Post by MAFoElffen on 2022-11-24
See attached pic... It still works with Gnome shell and Nautillus versions 43.0... The pic shows it executed from a ."desktop" file.

---

