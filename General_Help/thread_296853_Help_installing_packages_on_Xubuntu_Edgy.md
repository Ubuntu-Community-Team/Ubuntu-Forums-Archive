---
title: "Help installing packages on Xubuntu Edgy"
date: 2006-11-10
forum: General Help
---

### Post by h-delic on 2006-11-10
I´ve just installed Xubuntu Edgy Eft on to an ibook G3.  The installation went without hitch but I am unable to install packages on to it through Synaptic or Add/Remove.  When I click install I get this message:

> 
Please insert the disc labelled:
Xubuntu 6.10 _Edgy Eft_ - Release powerpc (20061025.1)
in drive /cdrom/](*,) 

The packages I have managed to install won´t open through the applications menu.

Thanks :-k :D

---

### Post by towsonu2003 on 2006-11-10
Note: I have no experience with powerpc

Couple of questions: 
[LIST]
[*]Do you have internet connection working[LIST]
[*]If yes, when you opened synaptic, did you click on "Refresh"?
[*]If no: synaptic tells you that it needs the installation CD to check for installable packages
[/LIST]
[*]Which packages (that are't shown in "application" menu) did you install, and how :)
[/LIST]

Also see [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) which might help you much quicker

---

### Post by dermotti on 2006-11-10
Sounds like you have references to the install CD in you sources.list

Post your /etc/apt/sources.list

---

### Post by JamesB on 2006-11-20
some of the dependencies are on the install cd. Just put the cd into the drive and synaptic will do the rest.

Hope this helps

James

---

