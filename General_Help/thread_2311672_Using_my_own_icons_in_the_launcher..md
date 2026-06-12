---
title: "Using my own icons in the launcher."
date: 2016-01-29
forum: General Help
---

### Post by moteprime on 2016-01-29
Hi there.
I make a lot of my own application shortcuts from chrome and put them in the launcher.
Recently i upgraded to Ubuntu 15.10 and several of my homemade webapp shortcut don't use the icons i assign to them but uses chromes own instead.

What i do is.
Load gmail in Chrome, and from the file menu i pick 'Create application shortcuts', tag 'Desktop' and 'Applications menu', and it saves the shortcut to the desktop.
I move the shortcut to a folder under my 'Documents', open the properties of the shortcut and change the icon from the default low-res icon to my own hi-res icon by clicking the icon in the properties box.
The shortcut keeps the icon, but when i run it (click) the default low-res icon are shown in the launcher, and that the one that i can lock to the launcher.
When i drag'n drop the shortcut to the launcher it get the hi-res icon, but when i click and start the application, another icon (the low-res) one shows up excatly the same way.

Se the attached image, gmail and pushbullet has the wrong icon, but google calendar has the right icon (this time).

[ATTACH=CONFIG]267010[/ATTACH]

This has worked fine from previous Ubuntus, but some have changed in 15.10.
How do i control the icons?

---

### Post by moteprime on 2016-02-04
I found them.
The 'real' app shortcut are located in /home/mads/.local/share/applications
Change the icons there, and they'll stick.

I'm proud of myself now, for finding out.
It's ok, since nobody cares.

---

