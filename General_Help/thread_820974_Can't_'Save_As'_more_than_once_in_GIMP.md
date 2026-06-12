---
title: "Can't 'Save As' more than once in GIMP"
date: 2008-06-06
forum: General Help
---

### Post by x1a4 on 2008-06-06
Hi,

I just noticed I can't use 'Save As' more than once in GIMP.  The first time I save a file it works great.  The second, and subsequent times, the 'Save Image' dialog is displayed but it's completely blank and none of the widgets show up.  When I close the image, then reopen it, I can 'Save As' again, but only once.

How do I solve this?

Thank you.

---

### Post by hal8000 on 2008-06-06
Not sure what version you are using but just tried this with Gimp 2.4.5 on Hardy 8.04 and you can save more than once.

I created a quick file called test.jpg , keeping image open I saved it again as test2.jpg and all was normal.

May I suggest starting gimp from the terminal, it may show useful output as to whats going wrong.

---

### Post by x1a4 on 2008-06-09
I'm using version 2.4.5 on Xubuntu Hardy.  

I started GIMP from the terminal and am only getting GTK warnings about some of the theme directories not having a size field.
```

(gimp:6947): Gtk-WARNING **: Theme directory 256x256/emblems of theme Industrial has no size field

(gimp:6947): Gtk-WARNING **: Theme directory 32x32/stock of theme Oxygen has no size field

(gimp:6947): Gtk-WARNING **: Theme directory 48x48/stock of theme Oxygen has no size field

(gimp:6947): Gtk-WARNING **: Theme directory 64x64/stock of theme Oxygen has no size field

(gimp:6947): Gtk-WARNING **: Theme directory 128x128/stock of theme Oxygen has no size field

```
The odd thing about these is that I have no GTK theme called Oxygen nor am I using it.  I have the Industrial theme but I'm not using it as well.  All of these warnings show up on GIMP start.

Another odd thing is that if I save the file in XCF format, I can 'Save As' as many times as I want.  When I try to save in another format like PNG, GIF, JPEG the 'Save Image' dialog becomes blank on the second and subsequent save attempts, until I close the image and open it again. 

If I save in PNM (Ascii) format, I can 'Save As' again.  If I save in PNM (Raw) format the same problem occurs. 

Other formats I tried
[size=-1](yes means I can 'save as' again, no means I can't)[/size]

Ascii (Pure HTML) -- yes
Win icon (compressed PNG) -- no
Win icon (uncompressed PNG) -- no
PBM (Raw) -- no
PBM (Ascii) -- no

Also, if I don't save, and click the 'Cancel' button, I can reopen the 'Save Image' dialog just fine.

EDIT: This applies to each image.  When I have two images open, I can 'Save As' one of them and then when I try to save it a second time the 'Save Image' dialog is blank.  If I then try to 'Save As' the second image I can do it, but only once.  Unless it's an XCF image.

---

### Post by lapubell on 2008-06-09
it might be a quirk.  not sure, but when I save as with a different extention (.jpg, .png or whatever) the export dialog shows up under the image.  I sometimes have to alt + tab to get that dialog up to the front and then it works fine.

Hope this helps.

---

### Post by x1a4 on 2008-06-18
> **lapubell said:**
> dialog shows up under the image.  I sometimes have to alt + tab to get that dialog up to the front and then it works fine.

The dialog doesn't loose focus, it's blank.  The window is drawn, but the widgets are not.

---

### Post by sc00ter on 2008-06-29
I can confirm this, using Gimp 2.4.5 on Hardy 8.04 LTS.

Using the Save option isn't the problem, it's when you attempt to **Save As** an image you've already saved (and is already open).

This happens **every time** when working with specifically .gif images.

I've attached a screen-grab to better demonstrate the issue.

**EDIT:**
I've added my experiences to the following Launchpad entry, which is the closest hit to this issue:
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/159778](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/159778)

---

### Post by bapoumba on 2008-06-29
I looked for bugs but did not find any realted. I just tried with a .png file, and had no problem saving it 3 times in a row with a different name, but could not save it to a different format more than once. I tried .gif, which worked, but could not save it as something else passed that.

Did you file a bug report ?

---

### Post by Seks on 2008-06-29
> **sc00ter said:**
> I can confirm this, using Gimp 2.4.5 on Hardy 8.04 LTS.

Using the Save option isn't the problem, it's when you attempt to **Save As** an image you've already saved (and is already open).

This happens **every time** when working with specifically .gif images.

I've attached a screen-grab to better demonstrate the issue.

**EDIT:**
I've added my experiences to the following Launchpad entry, which is the closest hit to this issue:
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/159778](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/159778)

I'm having the exact same problem as you and the OP, same version of gimp and hardy lts.

---

### Post by bapoumba on 2008-06-29
Does not look video driver related, as I have an intel chipset and no proprietary drivers. Are you all using compiz?

---

### Post by x1a4 on 2008-06-29
I don't know what I did (or didn't do) but this seems to have fixed itself.  I ran GIMP from the GNU debugger and everything worked.  I tried without it and it works.  The only change I've made is that I removed the debug symbols from the main repositories (gimp-dbg) and installed the ones from the debug repositories (gimp-dbgsym).  I don't think that that's it though.  I also installed some GTK updates recently, maybe one of them was the culprit?  I'll keep testing and keep this thread updated should I figure out what's what.

EDIT: I'm playing around with it, and sometimes it works, other times the 'Save As' dialog is blank.  Once I've found a discernable pattern I'll let you all know.

---

### Post by x1a4 on 2008-06-29
Found a pattern--although it's not very helpful at the moment.

open GIMP
from the menu, debugger or 'Run' dialog--it doesn't matter.

open an xcf file, regardless if I use the 'Open' dialog or the 'Open Recent' menu.

I 'Save As'  and in the 'Save Image' dialog I change the extension of the file name from xcf to png and click 'Save'

I don't touch the 'Save as PNG' dialog and click 'Save'

The image saves and I can 'Save As' again and again as long as I don't change any of the PNG properties.  If I do, the next 'Save As' attempt shows a blank 'Save Image' window.  

If I close the image, reopen it, I can 'Save As' only once, even though I haven't touched the PNG settings, which have been retained from previous save.  

If I try to save PCX, XPM, XBM, GIF or JPG (with or without modifying the save properties) the 'Save Image' dialog shows-up blank on the second attempt.

Debugger only shows the GTK warnings (see post #3)

I'll try with a different GTK theme.

---

### Post by x1a4 on 2008-06-30
I've been doing some looking around in Bugzilla, and this most likely is a GTK issue, not a GIMP issue.  Under certain circumstances, when configured just the wrong way, the GTK file chooser dialog crashes.

---

