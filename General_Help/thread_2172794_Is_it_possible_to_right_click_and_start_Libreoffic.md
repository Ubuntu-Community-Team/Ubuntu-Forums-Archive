---
title: "Is it possible to right click and start Libreoffice?"
date: 2013-09-06
forum: General Help
---

### Post by lile001 on 2013-09-06
A right click in Nautilus can start a text document and so on.  Is it possible to make a right click start a Libreoffice document in the selected folder?  Right now, I always end up surfing down to the folder I already have open when starting a new Libreoffice document, and it becomes a big timewaster after the 20th time in a day.  

Running Ubuntu 12.04 LTS with Gnome Classic

---

### Post by CaptainMark on 2013-09-06
Back in my gnome days, if you had a file in the ~/Templates directory nautilus would allow you to open a copy of it in the current directory via the right click menu, so place a blank libreoffice document in ~/Templates and hopefully that might do what you want

Alternatively someone has posted a very similar question on ubuntu answers [http://askubuntu.com/questions/21953/how-to-customize-the-context-menu-in-nautilus](http://askubuntu.com/questions/21953/how-to-customize-the-context-menu-in-nautilus)

---

### Post by bluefrog on 2013-09-06
open a new document with libreoffice writer
save it as it is in ~/Templates with the name writer for example.

now, if you right click in a folder and select create new document you will see an entry writer

can do that for a calc file and so on.

---

### Post by CaptainMark on 2013-09-06
> **bluefrog said:**
> open a new document with libreoffice writer
save it as it is in ~/Templates with the name writer for example.

now, if you right click in a folder and select create new document you will see an entry writer

can do that for a calc file and so on.
A glitch in the matrix!

---

### Post by lile001 on 2013-09-06
I don't find a folder called ~/Templates or ~/templates or ~/.templates.  Do I create one, and if so where? Or perhaps I don't know exactly how to look. Not very skilled at using Terminal.   I do find one at /usr/lib/libreoffice/share/template, is that what is being referred to?

---

### Post by lile001 on 2013-09-06
Here is a possible answer:

[http://askubuntu.com/questions/94734/what-is-the-templates-folder-in-the-home-directory-for](http://askubuntu.com/questions/94734/what-is-the-templates-folder-in-the-home-directory-for)

I have done this: 

> [COLOR=#333333][FONT=UbuntuRegular]If you have deleted the folder and need to restore this functionality:[/FONT][/COLOR]
gedit ~/.config/user-dirs.dirs
[COLOR=#333333][FONT=UbuntuRegular]Check that there is a line containing the following - if not, add this line.[/FONT][/COLOR]
XDG_TEMPLATES_DIR="$HOME/Templates"

Let's see if that is the trick.

---

### Post by lile001 on 2013-09-06
Awesome!  Worked immediately without reboot or anything!  The power of Linux....

---

