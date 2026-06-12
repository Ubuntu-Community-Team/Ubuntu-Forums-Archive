---
title: "'Open With' Photoshop in KDE? How do I do this?"
date: 2008-02-04
forum: General Help
---

### Post by Zeroangel on 2008-02-04
Hey all. I have had photoshop installed for the longest time but I would like to be able to open files from Konqueror without first having to open PS and navigate to folders.

Anyone know a quick way to do this?

What I've tried is navigating to the folder in Konqueror, right clicking on the image, and selecting 'open with'

But whenever I select the command:
```
wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe"
```as the open with command the terminal outputs something like
```
wine: could not load L"Z:\\home\\dave\\Pictures\\Webcam_Pictures\\wolf-decal.jpg": Bad EXE format for
```Any ideas?

For those GNOME users, if you have any thing to share which might work I would greatly appreciate this too since a similar method would work with KDE or GNOME.

---

### Post by Zeroangel on 2008-02-05
*bump!*

---

### Post by Zeroangel on 2008-02-06
*bump2!*

---

### Post by SOULRiDER on 2008-02-06
Check this out:
[http://legroom.net/2007/04/20/adding-custom-actions-kde-context-menus](http://legroom.net/2007/04/20/adding-custom-actions-kde-context-menus)

---

### Post by Zeroangel on 2008-02-06
Aww thanks man! This is so cool that I can now have photoshop in my context menu and this saves me much frustration because I use Photoshop all the fricken time. 

So here ya go. A star of VALOR, to show how much your tip made my day. :KS

FYI: This is my desktop file
```
[Desktop Entry]
ServiceTypes=image/gif,image/jpeg,image/jpg,image/png,image/x-bmp,image/x-vnd.adobe.photoshop
Actions=photoshop

[Desktop Action photoshop]
Name=Edit with Photoshop
Exec=wine "C:\Program Files\Adobe\Photoshop 7.0\Photoshop.exe" Z:%f
GenericName=Edit this file with Photoshop 7
Icon=/home/dave/Programs/cc22_photoshop.0.xpm
MimeType=image/gif;image/jpeg;image/jpg;image/png;image/x-bmp;image/x-vnd.adobe.photoshop
```For those of you who have similar issues, this will work for ya, with a few tweaks of course. :)

---

### Post by jrharvey on 2008-02-06
could you not simply open the search tool and type in (.PSD)??????

---

### Post by Zeroangel on 2008-02-06
Huh? Can you be a little more detailed than that?

I use photoshop for a lot of JPEGs too -- which are more or less scattered in different places. It is faster to navigate to the folder, right click, open with photoshop -- rather than using the search tool or photoshop's built in file browser.

---

### Post by Zeroangel on 2008-02-06
Also double-clicking on the PSD files tends to open photoshop but with an error "cannot read /home/whatevermypathis/file.psd because of disk error". I prepended Z: in the context menu shortcut to get around that.

Though it would be interesting to find out how to get at the MIME handler so I can do that with that as well...

---

### Post by jrharvey on 2008-02-08
What version of Photoshop are you using? Just curious.

---

### Post by Zeroangel on 2008-02-09
Photoshop 7

(EDIT: for politeness)

---

### Post by Psyphre on 2008-03-22
Hi, I am trying to do something similar with GNOME.
I wat to be able to rightclick a picture file (e.g jpg or png) and select "open with" photoshop. Is that what you were able to do?

---

