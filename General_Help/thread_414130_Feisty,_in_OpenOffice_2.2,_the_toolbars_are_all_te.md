---
title: "Feisty, in OpenOffice 2.2, the toolbars are all text no icons?"
date: 2007-04-19
forum: General Help
---

### Post by statictonic on 2007-04-19
I just got done installing Feisty and the toolbars in OpenOffice seem to be all text instead of icons.  Anyone know how to change it to be icons?  I did make some changed in gnome for the toolbars, tried changing them back incase it did something but didn't help.

---

### Post by statictonic on 2007-04-19
Anyone any ideas...?

---

### Post by rbmorse on 2007-04-19
tools > options > views

make sure there is a check in the box "show icons in menus"

---

### Post by IgnacioMiller on 2007-04-19
I'm having the same problem, and that box is checked for me.

---

### Post by statictonic on 2007-04-19
> **rbmorse said:**
> tools > options > views

make sure there is a check in the box "show icons in menus"

It is checked, i tried unchecking and rechecking it again.  Didn't help at all I went through and all the options seem to be set correctly for it that I could find anyways.

---

### Post by statictonic on 2007-04-19
I also just tried deleting ~/.openoffice.org2 so it would generate new settings files, still no icons.

---

### Post by ember on 2007-04-19
It happens, I think, when you change the icon theme (which I did). Try installing, e.g. the tango icon-theme for OO.

---

### Post by statictonic on 2007-04-19
> **ember said:**
> It happens, I think, when you change the icon theme (which I did). Try installing, e.g. the tango icon-theme for OO.

It already showed the tango theme as available I tried switching to it didn't help.  I also tried resetting back to the default theme for gnome in ubuntu, and that did not help either unfortunately.

---

### Post by mbjsscn2 on 2007-04-20
> **statictonic said:**
> I just got done installing Feisty and the toolbars in OpenOffice seem to be all text instead of icons.  Anyone know how to change it to be icons?  I did make some changed in gnome for the toolbars, tried changing them back incase it did something but didn't help.

This is a problem that seemed to crop up in the last few builds before release. Until a proper patch is released (or someone suggests an easier work round!) the answer for me was to uninstall all the openoffice components using Adept/Synaptic and then reinstall openoffice from the repros using 'sudo apt-get install openoffice.org'. Although quite a long winded process this also fixes the problems I was having with the openoffice bibliographic database. This was causing openoffice to crash out. BTW using this method there is no need to delete/alter your profile information in ~/.openoffice2.org.

Hope this helps
chris

---

### Post by maka on 2007-04-20
i had this problem too. but i was able to fix it by changing the icon type:

tools->options, view, and i selected human which worked for me.

---

### Post by UI-Freak on 2007-04-20
The problem is that the icon theme of your choice is NOT installed. Only 'human' is installed by default.
[B]
Install these packages:
[/B]
openoffice.org-style-default
openoffice.org-style-andromeda
openoffice.org-style-crystal
openoffice.org-style-industrial
openoffice.org-style-tango

These icon sets should have been installed as well to avoid the problems we had. That is what an update features should take care of.

---

