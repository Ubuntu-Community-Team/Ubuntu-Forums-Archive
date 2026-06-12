---
title: "Right click print"
date: 2023-05-09
forum: General Help
---

### Post by suomalainen on 2023-05-09
Hello My Friends!!!!

I have Ubuntu 22.04 and I would like to know how I can right-click on a file name (pdf, doc etc..) and select the 'print' option to print the file automatically.


I know it can be added via terminal I just don't know how to do it.


I would also like to learn how I can right click on a folder name and print automatically all the pdf files in the folder.

Could someone help me please?

Thank you!

---

### Post by Tadaen_Sylvermane on 2023-05-09
I like this idea. If it doesn't exist it would be a nice feature to work on. If i had more than super entry level programming experience I'd tackle it myself.

---

### Post by suomalainen on 2023-05-15
Bump!!!!!!!!!!!!!!!!!!!!

---

### Post by Holger_Gehrke on 2023-05-16
Since I use XUbuntu, I don't know whether nautilus - the Gnome file manager - still has that capability, but there used to be something called "user actions". Basically those are scripts that are assigned to options in the context menu and to file types either described as Mime-types or as globs. In Thunar - the filemanager of XFCE - this capability is available and works quite nicely. So you could define a script that shows up as a 'Print'-option in the menu for known file types and would call a command to print them - probably 'lpr %F' or something like that ...

Holger

---

### Post by yancek on 2023-05-16
Different options for different Desktop environments so which are you using?  The link below shows how to use a script to add it if you install nautilus-scripts.  The site is from 2016 but uses a script so should be workable.

[http://installfights.blogspot.com/2016/02/printing-multiple-files-from-right.html](http://installfights.blogspot.com/2016/02/printing-multiple-files-from-right.html)

>  I would also like to learn how I can right click on a folder name and print automatically all the pdf files in the folder.


Doubt that will happen as it requires software that is telepathic or do you mean having an option to print pdf files when right clicked?  See the link above.

---

### Post by suomalainen on 2023-05-23
Bump.... Would love to get this working with 22.04LTS!!!

Help please.

---

