---
title: "Generic Linux icon (instead of original program icon per running instance)"
date: 2022-01-08
forum: General Help
---

### Post by enzmannd on 2022-01-08
I installed the proprietary statistics software Stata on Ubuntu 20.04 following the Stata installation guide (see [https://www.stata.com/manuals/ig.pdf](https://www.stata.com/manuals/ig.pdf) ).

The problem: When starting Stata (xstata-se) the generic Linux icon for a running  application (instead of the original Stata icon) is shown and multiple instances  of Stata appear "under" the same (single) icon (see the bottom left part of the screenshot attached). Strange enough: When  starting a different version of the program (i.e. "xstata" instead of "xstata-se"), everything is OK: There is one  original Stata icon per running instance of Stata.

Note that it does not matter whether I start the program from the terminal or via a desktop link (Stata17.desktop).

I already asked for Stata's technical support but they can't help: "We have not had any other reports of this behavior, were you able to get a response from Ubuntu forum about this issue?"

Any idea why this happens and how to solve the issue?

---

### Post by KBar on 2022-01-08
Could you post the content of its desktop entry? By default, they're located in */usr/share/applications* or in *$HOME/.local/share/applications*. If it's not there, check its directory, which is */usr/local/stata17* recommended in the guide.

---

### Post by enzmannd on 2022-01-08
Here is the desktop entry, but as I said, the behavior also occurs if I start the program from the terminal window:

---- (start "Stata17.desktop": ) ----

[Desktop Entry]
Version=17.0
Terminal=false
Icon=/usr/local/stata17/stata17.png
Type=Application
Categories=Education;Scientific;
Exec=/usr/local/stata17/xstata-se
Name=Stata/SE 17.0
Comment=Perform statistical analyses using Stata.
StartupNotify=true
MimeType=application/x-stata-dta;application/x-stata-do;application/x-stata-smcl;application/x-stata-stpr;application/x-stata-gph;application/x-stata-stsem;
Actions=doedit;use;view;graphuse;projmanag;semopen;

---- (end "Stata17.desktop".) ----

The file is located in ~/home/desktop/

---

### Post by enzmannd on 2022-01-08
Thanks for your help -- your suggestion to the location of the desktop entry helped to identify the problem:

I looked also in other folders to find .desktop-files for Stata and found the file "xstata-se.desktop" in *~/home/.local/share/applications* . Its content is:

---- (start "xstata-se.desktop": ) ----

[Desktop Entry]
Exec=/usr/local/stata17/xstata-se
MimeType=application/x-stata-dta;
Name=xstata-se
NoDisplay=true
Type=Application

---- (end "xstata-se.desktop".) ----

I renamed the file to "xstata-se.desktop_orig" (to stop being used) and now the issue is solved! 

I assume that ```
NoDisplay=true
``` was the culprit -- am I correct?

By the way: How do I mark the thread as being solved?

---

### Post by KBar on 2022-01-08
> **enzmannd said:**
> By the way: How do I mark the thread as being solved?

In the upper right corner of your thread:

---

