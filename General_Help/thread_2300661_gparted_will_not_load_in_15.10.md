---
title: "gparted will not load in 15.10"
date: 2015-10-27
forum: General Help
---

### Post by sammiev on 2015-10-27
Worked great till a few days ago.

Can load parted in Terminal with no issues.

Anyone else?

---

### Post by gedakc on 2015-10-27
There is a bug report open for this issue:

[Bug 1509729 - gparted does not start, crashes with library symbol lookup error]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1509729")

From reading the report, the problem appears to affect more than just GParted and might be an issue with the ubuntu package of glibmm-2.4.  The glibmm-2.4 library is used by many other projects.

---

### Post by findingthebalance on 2015-10-27
I did not experience the problem with Gparted, but I did with a few other programs since updating to Ubuntu 15.10, the programs would start from terminal though. What I did was uninstall the program then use Synaptic package manager to fully remove then reinstall and restart the computer and that fixed it for me. I am thinking it's because I upgraded from 15.04 to 15.10 rather than a clean install like I usually do.

Cheers

---

### Post by sammiev on 2015-10-27
> **findingthebalance said:**
> I did not experience the problem with Gparted, but I did with a few other programs since updating to Ubuntu 15.10, the programs would start from terminal though. What I did was uninstall the program then use Synaptic package manager to fully remove then reinstall and restart the computer and that fixed it for me. I am thinking it's because I upgraded from 15.04 to 15.10 rather than a clean install like I usually do.

Cheers

Thanks for the reply.

I have removed gparted yesterday and did a fresh reinstall of the package. Still the same.

My install of 15.10 was a fresh install from Sunday and not an upgrade.

---

### Post by kryten35 on 2015-10-27
Im running  a fresh install of Ubuntu Gnome 15.10(64bit) and gparted launches with no problems both in/outside of terminal.
Not found any problems with other apps.

Did you run check disc for errors before the install?

---

### Post by sammiev on 2015-10-28
It's likely something with gnome. Are you running gnome?

---

### Post by coldraven on 2015-10-28
> **kryten35 said:**
> Im running  a fresh install of Ubuntu Gnome 15.10(64bit) and gparted launches with no problems both in/outside of terminal. Not found any problems with other apps.  Did you run check disc for errors before the install? Same here, no problems so far.

---

### Post by sgage on 2015-10-28
I'm running 15.10 (Ubuntu Gnome), and everything is working fine, including gparted. This is an installation clean-installed from the Daily Build of 10/16 and updated right through into the release version.

---

### Post by kryten35 on 2015-10-28
> **sammiev said:**
> It's likely something with gnome. Are you running gnome?
Yes my previous post states that im using the Gnome desktop.

Used  "erase disk and install ubuntu" from a LIVE ubuntuGnome 15.10 iso image, shortly after it was released.

---

### Post by sammiev on 2015-10-30
> **kryten35 said:**
> Yes my previous post states that im using the Gnome desktop.

Used  "erase disk and install ubuntu" from a LIVE ubuntuGnome 15.10 iso image, shortly after it was released.

Gparted was working after I did a fresh install of 15.10 and works great with 16.04

The problem started after 15.10 was updated.

Both 15.10 and 16.04 are running the exact same programs.

---

