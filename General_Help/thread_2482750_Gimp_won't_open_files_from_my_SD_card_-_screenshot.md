---
title: "Gimp won't open files from my SD card - screenshot included"
date: 2023-01-09
forum: General Help
---

### Post by jonfisher on 2023-01-09
Gimp won't open files from my SD card - screenshot included

If I copy the folder, of files, to the computers desktop, I can then open them with no problem

screenshot attachment included below

Addendum:  The "write to" switch on side of SDHC card has nothing to do with this, as I've tested it with it on/off

---

### Post by TheFu on 2023-01-09
If the gimp program is a snap package, you've just learned about the wonderful constraints of snap packages.  These constraints prevent access to most of the file system. By default, only the user's HOME directory can be accessed.

There is good news.  It is possible for many snap packages to be allowed to access storage under /mnt/ and /media/ which is likely where temporary storage is mounted.  I don't know if the gimp snap package allows this, but many do.
The usually command would be something like this:
```
$ snap connect gimp:removable-media
```
That should work. Can't hurt to try it.

---

### Post by jonfisher on 2023-01-10
> **TheFu said:**
> If the gimp program is a snap package, you've just learned about the wonderful constraints of snap packages.  These constraints prevent access to most of the file system. By default, only the user's HOME directory can be accessed.

There is good news.  It is possible for many snap packages to be allowed to access storage under /mnt/ and /media/ which is likely where temporary storage is mounted.  I don't know if the gimp snap package allows this, but many do.
The usually command would be something like this:
```
$ snap connect gimp:removable-media
```
That should work. Can't hurt to try it.


That terminal command worked.  I thought that maybe I'd have to enter that into terminal each time I started to the computer; however, I restarted the computer and it can still open files from the SD card.

Thanks!
problem solved

---

### Post by jonfisher on 2023-01-10
I have marked this thread as solved & will move on.

However, I do find this to be quite ridiculous....

---

### Post by Impavidus on 2023-01-10
> **jonfisher said:**
> However, I do find this to be quite ridiculous....

You're not alone.

Gimp is still available as a deb package on 22.04.

---

### Post by TheFu on 2023-01-10
> **jonfisher said:**
> That terminal command worked.  I thought that maybe I'd have to enter that into terminal each time I started to the computer; however, I restarted the computer and it can still open files from the SD card.

Thanks!
problem solved

There are some good reasons for snap packages, but 1-size never fits everyone. Canonical has forgotten that lesson with Firefox and Chromium browsers.  For example, I mount network storage under /d/, not /media/ ... because I'm following the mount location standards in the LFSH document.  The fact that Snaps don't allow local control for which locations can be used for HOME directories and which locations can be accessed by constrained programs is really the main issue I have with snap packages.  The forced upgrades of snaps is a problem too. If I wanted package updates to be forced, I'd still use MS-Windows or Google's ChromeOS which don't have a method to stop updates. That and trying to make server processes distributed only as snap packages.  

RedHat has a competing 1-file package distribution system called Flatpaks.  They use it for desktop programs, not server programs and allow local overrides for all the constraints.

Both flatpaks and snap packages are bloated and full of other reasons they aren't good for everyone.  I love there are options and can appreciate setups where they make sense.

Sigh.  Canonical has lost their way with snap packages.  Local controls really are mandatory.

---

