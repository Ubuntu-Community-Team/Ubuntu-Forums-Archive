---
title: "Dpkg: --path-exclude usage..."
date: 2018-02-03
forum: General Help
---

### Post by omelette on 2018-02-03
Hi.  I've got a couple of Linux apps that I built locally (gnome-disk-utility & handbrake) that I'm trying to install.  Thing is, they share a common file, so the second install always fails with a "broken pipe" error.  The shared file in question is;

**/usr/local/share/icons/hicolor/icon-theme.cache**

Using 'dpkg', when I try installing the app with the **--path-exclude=<pattern>** - in this instance;

*sudo dpkg -i gnome-disk-utility_3.12.1-1_i386.deb --path-exclude=usr/local/share/icons/hicolor/icon-theme.cache*

- I still end up with a "broken pipe" error message because it's;

**"trying to overwrite '/usr/local/share/icons/hicolor/icon-theme.cache', which is also in package handbrake 0.10.5-1"** 

My question, why is the dpkg --path-exclude option not working as one would expect?

---

### Post by steeldriver on 2018-02-04
Did you try

```

--path-exclude=[COLOR=#0000ff]**/**[/COLOR]usr/local/share/icons/hicolor/icon-theme.cache

```

---

### Post by omelette on 2018-02-04
> **steeldriver said:**
> Did you try

```

--path-exclude=[COLOR=#0000ff]**/**[/COLOR]usr/local/share/icons/hicolor/icon-theme.cache

```

Nope, doesn't make a difference.

I have even tried creating an 'excludes' file and adding;

**path-exclude=/usr/local/share/icons/hicolor/icon-theme.cache**

to;

**/etc/dpkg/dpkg.cfg.d/excludes**

- but it doesn't make a difference.  It still attempts to overwrite icon-theme.cache, with the resultant 'broken pipe' error.  I am obviously misunderstanding how --path-exclude is meant to be used.

Edit:
After thinking about this for a moment, this behaviour seems correct.  If it would allow what I am trying to achieve, I would then be unable to remove either app, at least 'normally', as the icon-theme.cache file would be a needed-dependency of the other.  So it seems that I can either do as I'm doing, remove the other app before installing the one I want to use, or recompile one to exclude the dependency-file. Rats!

---

