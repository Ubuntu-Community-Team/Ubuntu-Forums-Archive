---
title: "udev/rules.d in /etc and /lib"
date: 2014-12-18
forum: General Help
---

### Post by pwabrahams on 2014-12-18
The files /udev/rules.d appear in two places: /etc/udev/rules.d and /lib/udev/rules.d.  Why is that?  What determines whether a particular rule belongs in one place or the other?

---

### Post by deadflowr on 2014-12-18
From the README file in /etc/udev/rules.d:
> The files in this directory are read by udev(7) and used when events
are performed by the kernel.  The udev daemon watches this directory
with inotify so that changes to these files are automatically picked
up, for this reason they must be files and not symlinks to another
location as in the case in Debian.


Packages do not generally install rules here, this directory is for
local rules.  If you want to override behaviour of package-supplied
rules, which can be found in /lib/udev/rules.d, you can do one of
two things:


 1) Write your own rules in this directory that assign the name,
    symlinks, permissions, etc. that you want.  Pick a number higher
    than the rules you want to override, and yours will be used.


 2) Copy the file from /lib/udev/rules.d and edit it here; you
    should generally only do this if you want to prevent a program
    from being run.




If the ordering of files in this directory are not important to you,
it's recommended that you simply name your files "descriptive-name.rules"
such that they are processed AFTER all numbered rules in both this
directory and /lib/udev/rules.d and thus override anything set there.


Basically what happens is the system has a place where the package installs the configuration files it'll read, and then a place where additional configurations can be placed by the user.
A lot of programs do this, you might notice this behavior more in a different approach, where the "user-made" configurations are in the home folder(usually in a hidden folder like .config).

Hope this helps, a little...

---

