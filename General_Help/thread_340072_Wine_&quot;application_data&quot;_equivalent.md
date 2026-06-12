---
title: "Wine &quot;application data&quot; equivalent?"
date: 2007-01-16
forum: General Help
---

### Post by m0u53m4t on 2007-01-16
I'm running a program that requires "B2B86000.dat" to be in the directory \Documents & Settings\All Users\Application Data\Adobe Systems\Product licenses\

Where do I put that file for my program to work and it think that's the right place?

---

### Post by tito2502 on 2007-01-16
~/.wine/drive/drive_c/

is your Wine C drive.

---

### Post by m0u53m4t on 2007-01-16
So is this right?

drive_c/windows/profiles/yourname/application data/

---

### Post by majoridiot on 2007-01-17
> **m0u53m4t said:**
> So is this right?

drive_c/windows/profiles/yourname/application data/

open nautilus and set View-->Show hidden files... the virtual C drive is
in the hidden folder .wine and is generally under drive_c. the likely path to you need is:

~/.wine/drive_c/windows/profiles/All Users/Application Data/Adobe Systems/Product licenses/

---

