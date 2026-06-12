---
title: "Ubuntu Desktop 23.10 // several snap issues"
date: 2023-10-18
forum: General Help
---

### Post by alphaelwedritsch on 2023-10-18
Hello community,
I did a fresh installation of 23.10 on ky HP laptop. Did the minimal installation method.

My usecase is very simple:
browser - brave
office - libreoffice
nextcloud - nextcloud desktop app

I've installed all these three apps as snap version.

But:
brave:
I'm not able to set brave as default browser. Neither in gnome settings, nor in browser itself. Everytime I start the browser I get ask to set it as default browser.
Can't print. No printers detected
libreoffice:
Not able to print
nextcloud:
client cannot get access to my home folder to create nextcloud subfolder for sync

All of my three apps are not useable.

[FONT=-apple-system]The first experience with Ubuntu and Snap is therefore very disappointing[/FONT]

---

### Post by ian-weisser on 2023-10-18
[FONT=arial]A possible reason you cannot print:

> **alphaelwedritsch said:**
> Did the minimal installation method.

A minimal install may not include the printing stack. (some flavors do, some don't).
 Check that the "cups" package is installed. If not, install it plus dependencies.

> **alphaelwedritsch said:**
>  The first experience with Ubuntu and Snap is therefore very disappointing         

Let's not judge quite yet.
[/FONT]

---

### Post by Dennis N on 2023-10-18
> Can't print. No printers detected
Did you add your printer to your system? Settings > Printers > Add Printer (see screenshot)
Details of adding the printer vary with type - USB, ethernet, etc.
Mine is connected through my router. I enter the IP address, then it was discovered. (screenshot 2)
Select, and the driver was automatically found. Ready to go. (screenshot 3)
All the above on Ubuntu 23.10 (minimal).

---

### Post by grahammechanical on 2023-10-18
This is your first experience of Ubuntu and you have chosen the "put the pieces together yourself" version. Ubuntu Desktop comes with everything most users want and need. And a lot more than we actually use. That was the original purpose of the first developers of Ubuntu and that same design purpose continues with today's Ubuntu developers.

The minimal install is for those who have a special need for a small size, limited set of applications version of Ubuntu.

Regards

---

### Post by alphaelwedritsch on 2023-10-19
Thanks guys, all works fine, accept printing in snap app versions and file access in snap NC client.
printing works painless outside snap.
using brave and libreoffice as deb version, no issues at all. same for NC client

it's not my first experience of ubuntu, the first with snap.
using linux since 1998.

maybe somebody can try to reproduce the issues. 
i'm sure it does not depend on minmal installation method.

---

### Post by alphaelwedritsch on 2023-10-19
can install openboard as snap version, but after installation, there's no executable available...strange

---

### Post by ian-v on 2024-01-10
I had the same issue issue with printer and Libreoffice.

 Typing this in a terminal solved it for me ```
snap connect libreoffice:cups-control :cups-control
``` 

Requires root privileges so you may need to add [FONT=courier new]sudo[/FONT] in front of it

Source: [URL="https://ask.libreoffice.org/t/libreoffice-snap-package-doesnt-list-the-system-printers/27891"]https://ask.libreoffice.org/t/libreoffice-snap-package-doesnt-list-the-system-printers/27891

[/URL]

---

