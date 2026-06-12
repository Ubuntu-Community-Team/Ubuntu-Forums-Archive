---
title: "Install gtk +-2.0 and gthread-2.0"
date: 2007-06-04
forum: General Help
---

### Post by RelativelyQuantum on 2007-06-04
I have been trying for some time now to install two packages called gtk+-2.0 and gthread-2.0, neither of which I can find in Synaptic or Aptitude. Any information would be greatly appreciated.

---

### Post by RelativelyQuantum on 2007-06-04
I've tried installing them using terminal to no avail, and really don't know where to turn. Synaptic turned up nil, as did Add/Remove. Any information would help

---

### Post by MatthiasM on 2007-08-11
The Ubuntu Package Search or Synaptics is usually a good source:

[Ubuntu Package Search]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=libgthread&searchmode=searchword&case=insensitive&version=feisty&arch=i386"): packages libglib2.0-dev or libglib1.2-dev
[Ubuntu Package search]("http://packages.ubuntu.com/cgi-bin//search_packages.pl?exact=0&searchon=names&version=all&case=insensitive&release=all&keywords=libgtk&arch=any"): libgtk2.0-dev

You will found out that the package naming follows some guildelines with 
*-dev or lib* ... which makes it easier to guess the right dependencies.

---

