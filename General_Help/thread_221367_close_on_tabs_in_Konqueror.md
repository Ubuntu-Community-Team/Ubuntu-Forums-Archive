---
title: "close on tabs in Konqueror"
date: 2006-07-23
forum: General Help
---

### Post by TheRingmaster on 2006-07-23
Is there anyway to put a close tab button on each individual tab instead of having the "close current tab" button in the corner. keep in mind that I am using Konqueror.

---

### Post by NeoChaosX on 2006-07-23
Closest thing I can think of is to go into Konqueror's Preferences > Web Behavior > Advanced Options button, then put a checkbox on "Show close button instead of website icon", then restart Konqueror.

---

### Post by Jucato on 2006-07-23
That might be a bit confusing at first.

May I propose an alternative? Middle-click the tab to close it:

> Add the following text to your ~/.kde/share/config/konquerorrc and clicking on
 a tab with the middle mouse button will close it.
 
 
[quote]
[FMSettings]
 MouseMiddleClickClosesTab=true

[/quote]

Hope that helps.

---

### Post by hotweiss on 2007-12-03
Another easier way to close tabs with your middle mouse button is this:

> kwriteconfig --file konquerorrc --group "FMSettings" --key MouseMiddleClickClosesTab --type bool true

Just past that in terminal as one line.

---

