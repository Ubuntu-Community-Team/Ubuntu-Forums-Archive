---
title: "Enabling hidden files in the LibreOffice save/load dialog"
date: 2013-12-29
forum: General Help
---

### Post by Sworddragon on 2013-12-29
LibreOffice 4.1.x isn't showing me any hidden files in the save/load dialog as it uses its own dialog (so "org.gtk.Settings.FileChooser show-hidden true" doesn't work here). Does anybody know how to enable this feature?

---

### Post by damage3025 on 2013-12-29
Can Ctrl+H toggle whether hidden files are shown?
If you right-click in file listing part of the dialog, can you see "Show Hidden Files"?

---

### Post by Sworddragon on 2013-12-29
> **damage3025 said:**
> Can Ctrl+H toggle whether hidden files are shown?

No, this opens the LibreOffice help in a browser.


> **damage3025 said:**
> If you right-click in file listing part of the dialog, can you see "Show Hidden Files"?

There is not context menu if I don't right click on a file and on a file I have just the options to delete or rename it. But if I use the upstream version there is the gtk menu which contains this context menu entry.

---

### Post by Bucky Ball on 2013-12-29
What hidden file are you attempting to open exactly?

Open a regular file manager, right click on the hidden file, 'Open With ...'. Try choosing Libreoffice.

---

### Post by deadflowr on 2013-12-29
Are you trying to open a hidden file, or enable hdden files shown in libreoffice.
Then the advice above is right.
When enabling hidden files, go to "File" in the menu, then go to "Open"
Now in the box that opens right click in the main area, and it will show the show hidden files, then click on it to enable.

I don't know what area of libreoffice you're looking at that this isn't appearing in.
Are you perhaps looking in a preferences section?

---

### Post by Sworddragon on 2013-12-30
> **deadflowr said:**
> or enable hdden files shown in libreoffice.

This.


> **deadflowr said:**
> When enabling hidden files, go to "File" in the menu, then go to "Open"
Now in the box that opens right click in the main area, and it will show the show hidden files, then click on it to enable.

I don't know what area of libreoffice you're looking at that this isn't appearing in.
Are you perhaps looking in a preferences section?

As I said this works in the upstream version (so I'm definitely not clicking at the wrong area) but not in the ubuntu version. Maybe it is just a bug, I will make a report later if there is really no solution.

---

### Post by damage3025 on 2013-12-30
@Sworddragon

My suggestions given above works for me on Ubuntu trusty (14.04 alpha at the time of writing), official repository version of LibreOffice 4.1.x.

What is your Ubuntu version? Are you using upstream LibreOffice or official repository LibreOffice or PPA LibreOffice?

---

### Post by deadflowr on 2013-12-30
> **Sworddragon said:**
> As I said this works in the upstream version (so I'm definitely not clicking at the wrong area) but not in the ubuntu version. Maybe it is just a bug, I will make a report later if there is really no solution.

What version of Ubuntu are you running?
Works fine on saucy and trusty for me.
Don't use a ppa though, so don't know how well that works.
And precise is still super old, so...

---

### Post by Sworddragon on 2013-12-30
I'm on Trusty too with LibreOffice from the official Ubuntu repository (1:4.1.3-0ubuntu2). Here is a screenshot how it looks on my system: [http://img1.picload.org/image/lggcpai/2013_12_30_23_31.png](http://img1.picload.org/image/lggcpai/2013_12_30_23_31.png)
Clicking below 'VirtualBox VMs' with a right click causes nothing to happen. But if I use the upstream version it works (also the menu looks completely different there). Maybe it is just a theme issue or something else as I'm on LXDE?

---

### Post by mc4man on 2013-12-30
Likely because you're using lo without gnome/gtk support, that's why you're getting that crappy looking open dialog window
if desired install the top package which should also bring in the other 2
libreoffice-gnome 
libreoffice-gtk 
libreoffice-style-human

---

### Post by Sworddragon on 2013-12-30
Installing libreoffice-gtk does solve the issue. But what if somebody doesn't like the GTK+ look (as the toolbar does visually change too), is there also a way to do this for the fallback menu?

---

### Post by mc4man on 2013-12-30
> **Sworddragon said:**
> Installing libreoffice-gtk does solve the issue. But what if somebody doesn't like the GTK+ look (as the toolbar does visually change too), is there also a way to do this for the fallback menu?
Doesn't appear to be any way if not using that gtk package, at least as seen here in 14.04

---

