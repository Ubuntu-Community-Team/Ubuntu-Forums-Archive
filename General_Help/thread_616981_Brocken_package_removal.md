---
title: "Brocken package removal"
date: 2007-11-18
forum: General Help
---

### Post by dziemecki on 2007-11-18
I appear to have a partially installed package (firefox-alt-widgets, if that matters) that's clogging up apt-get/adept.  Everytime I install something, it's hit or miss whether or not this partial install will pop up and hose the process with something like:

```

Removing firefox-alt-widgets ...
rm: cannot remove `/usr/lib/mozilla-firefox/res/forms.css': No such file or directory
dpkg: error processing firefox-alt-widgets (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firefox-alt-widgets
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried to "--purge remove" it to no avail.  Any ideas on how to clean this thing out?

---

### Post by Thyme on 2007-11-19
Doesn't dpkg have a "force" remove option? I would try and re-create those files and then remove or re-install firefox to install whatever files are missing and then remove.

---

### Post by dziemecki on 2007-11-19
> **Thyme said:**
> Doesn't dpkg have a "force" remove option? I would try and re-create those files and then remove or re-install firefox to install whatever files are missing and then remove.

Not familar with "dpkg".  Is that related to "apt-get remove"?

And just to be clear, "firefox-alt-widgets" is not part of the Firefox package.  It's a 3rd party hack.  Are you still suggesting I reinstall firefox?  I should also note that "/usr/lib/mozilla-firefox" is not the current firefox install directory, so there will *never* be anything in there.

---

### Post by Thyme on 2007-11-19
Hi dziemecki,

dpkg is the original package menagement system for deb files but since it doesn't handle dependencies apt was created. I think add/remove is just a front-end to apt or dpkg for easier use ..

Try playing around with dpkg:

The following will show you what dpkg is capable of:

```

dpkg --help

```

The following lists all the packages installed on your system:

```

dpkg -l

```

Anyway, the second line in the code you posted means that add/remove is trying to remove firefox from /usr/lib/mozilla-firefox and since you say it's empty, installing firefox their will maybe stop this error.

Alternatively, and which I think is easiest, just use dpkg to remove the "firefox-alt-widgets" package with a "force" option. In almost all cases, a force option tells the command to ignore any errors and continue doing whatever it must to to finish.

I'm not sure but the following may remove the "firefox-alt-widgets" package:

```

dpkg -rf firefox-alt-widgets

```

Cheers :)

---

### Post by dziemecki on 2007-11-20
The force-remove ended up giving me the exact same error.  I "fixed" it by putting files where it wanted to remove them.  

Guess "force" isn't all that forceful.

---

