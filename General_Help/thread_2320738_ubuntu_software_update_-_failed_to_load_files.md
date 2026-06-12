---
title: "ubuntu software update - failed to load files"
date: 2016-04-16
forum: General Help
---

### Post by schmitta on 2016-04-16
for update I got: ubuntu software update - failed to load files

My internet connection is being used for music and works fine for everything else.

I looked it up and then changed the edit>source location to the united states source and got:

failed to load repository information and the details said:

W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file), E:Some index files failed to download. They have been ignored, or old ones used instead.

I am using Ubuntu 14.04 LTS and need the updates to keep current. This has been going on for several months. How do I update to current level for 14.04?

---

### Post by deadflowr on 2016-04-16
It's the fact that google chrome dropped support for 32-bit(i386) versions for linux that's causing your error/warning.
The design of googles sources.list looked for packages for both 64-bit and 32-bit, regardless of what version you ran.

Easy fix, choose between two methods, really.
easy or not as easy.

Easy: Download a fresh version of chrome from google chrome's web site.
Uninstall the version you have, and reinstall the new version.

Not as easy: edit the google chrome sources.list file in
/etc/apt/sources.list.d/google-chrome.list
and change the line from
```
deb http://dl.google.com/linux/chrome/deb/ stable main
```
to
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
then re-run the updater.

Note that if you are running a 32-bit system, then forget about any of this and uninstall google chrome.
As 32-bit google chrome on linux will never be updated ever again, and should now be considered unsafe.

---

