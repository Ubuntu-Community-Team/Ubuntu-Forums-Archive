---
title: "Unity doesn't load, no Launcher, no Dash appears when using startx"
date: 2014-06-24
forum: General Help
---

### Post by tubos2 on 2014-06-24
- I've edited my grub and changed to boot into text mode and ran sudo update-grub

- everything works but when I use startx to launch x unity doesnt load, no dash etc.
  just the ubuntu background with some file icons , CTRL ALT T still works.

- I'm using LTS 14.04 how can I fix this?

---

### Post by whitesmith on 2014-06-24
This may not fix your problem, but it can't hurt it either```
apt-get update && apt-get upgrade
``` The man page for update says:```
update is used to resynchronize the package index files from their
           sources. The indexes of available packages are fetched from the
           location(s) specified in /etc/apt/sources.list. For example, when
           using a Debian archive, this command retrieves and scans the
           Packages.gz files, so that information about new and updated
           packages is available. An update should always be performed before
           an upgrade or dist-upgrade. Please be aware that the overall
           progress meter will be incorrect as the size of the package files
           cannot be known in advance.
```
For upgrade it says:```
upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.
```

---

### Post by 3rdalbum on 2014-06-25
> **tubos2 said:**
> - I've edited my grub and changed to boot into text mode and ran sudo update-grub

- everything works but when I use startx to launch x unity doesnt load, no dash etc.
  just the ubuntu background with some file icons , CTRL ALT T still works.

- I'm using LTS 14.04 how can I fix this?

Don't use 'startx'. Use this:

```
sudo service lightdm start
```

---

### Post by tubos2 on 2014-06-25
> [COLOR=#000000]
Don't use 'startx'. Use this:[/COLOR]

[COLOR=#000000]Code:

sudo service lightdm start
[/COLOR]

Thank you , your tip worked great , any way to fix startx ?

---

