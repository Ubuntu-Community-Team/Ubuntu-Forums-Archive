---
title: "[SOLVED] kdissert &amp;amp; semantik problem"
date: 2008-05-18
forum: General Help
---

### Post by jflaming on 2008-05-18
OK, I'm going crazy here.  I am trying to create some mindmaps that will lead to LaTeX documents.  I have used Kdissert in the past, and really liked it.  I installed the version in the HH repository, and it works, but it generates obsolete LaTeX code (I can't get it to compile on the current TeXLive distribution in the repo... various errors). 
Anyway, I looked up kdissert and found that is deprecated.  The new software is Semantik.  I used aptitude to install Semantik, although the version in the repos is 3 versions out of date.  It shows up as installed, but it won't launch. If I launch it at the CLI, I get a "Command not found" error.  It appears to me that the binary is not present, or at least I can't find it.  

So... I downloaded the source code to the new version and tried to install from source.  However, I haven't been able to resolve all the dependency problems (KDE4 and QT packages).  I can't seem to get them all resolved.  

I feel like I'm stuck... any suggestions?  Right now I'm copying and pasting the LaTex output code core bits from the old Kdissert into fresh empty text and re-writing the LaTex wrapper, but this seems a bit silly.

Edit:
I have gotten semantik to compile by solving most of the dependency issues.  Particularly the kde4-config problem, solved here: 
[http://ubuntuforums.org/showthread.php?t=642298](http://ubuntuforums.org/showthread.php?t=642298)
Also troublesome was an unpublished dependency on gettext, which isn't fully installed by default in HH.

---

