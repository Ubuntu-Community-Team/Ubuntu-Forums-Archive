---
title: "Open Office Crashes on Customize Toolbar (Gutsy)"
date: 2007-10-16
forum: General Help
---

### Post by abrichr on 2007-10-16
Any application in the Open Office suite crashes when I click on "customize toolbar".

It all started after upgrading to Gutsy, the icons were no longer there, so I reinstalled them.  The icons are back, but clicking "Customize Toolbar" results either in the window freezing, followed by a dialog reporting that Open Office has stopped responding, or in the window closing, and Open Office Recovery Wizard taking its place.

I've already tried reinstalling every Open Office package I have installed.  Any suggestions?

---

### Post by Lemons on 2007-10-16
Well, it might not be Open Office. Since Open Office is built on java, check if your java version is a beta. I have the same problem, except I cant get the icons to work. Also this shows in eclipse, where many things will just suddenly crash it.

I have no idea how to downgrade though, I wish I did... I want my java working correctly ;_;

---

### Post by abrichr on 2007-10-16
In Synaptic, package openoffice.org-java-common is version 1:2.3.0=1ubuntu5, which is the latest version.  I reinstalled it, but still the same problem.  I don't use any other programs that i know of which are java based.

It's not just the customize button, either.  I went to change the orientation of the page in the printer settings entry in the file menu, and it crashed.

This is extremely frustrating....

---

### Post by s4lv1n0 on 2007-11-15
Hi folks! I had exactly the same problem. I just removed the "openoffice.org-gnome" package and everything is working fine. BUT I got that ugly "grayish Windows 98" Java interface on OpenOffice. It's not the best solution but works.

```
sudo aptitude purge openoffice.org-gnome
```

It will also automatically remove others packages that won't be used anymore, it's safe to do this.

I hope this works for you people!

---

