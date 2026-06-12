---
title: "Debian Package problem"
date: 2005-05-27
forum: General Help
---

### Post by talon on 2005-05-27
I have a problem running debian packages, when I click on them, it comes up with a basic error message. Can't remeber exactly what it says. Anyone else had this problem and know how to fix it?
Cheers

---

### Post by bored2k on 2005-05-27
[QUOTE=talon]I have a problem running debian packages, when I click on them, it comes up with a basic error message. Can't remeber exactly what it says. Anyone else had this problem and know how to fix it?
Cheers[/QUOTE]
 To install .deb packages, you to run them from the command line
[sudo dpkg -i file.deb]

---

### Post by talon on 2005-05-27
ah, n00b problem then....................cheers!

---

### Post by 23meg on 2005-05-27
there is a gui .deb installer that will let you install debian packages with a double click, see [this thread](http://www.ubuntuforums.org/showthread.php?t=28650&highlight=deb+installer).

---

### Post by az on 2005-05-27
It would be altogether better to find an ubuntu repository with the package you need and add it to your synaptic list...

that will avoid a lot of headaches!  If the package won't install like that, it is because it will bork your system otherwise..

---

