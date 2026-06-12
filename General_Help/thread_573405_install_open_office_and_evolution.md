---
title: "install open office and evolution"
date: 2007-10-11
forum: General Help
---

### Post by tomerl on 2007-10-11
Hi, 

I know that Open Office and Evolution comes by default in almost any linux distro, 
and i also know that the easy way to install both of them is from the synaptic gui... 
but for I would like to know to master linux, and therefor I'd like to know what is the command line of installing both of them.
Any help will be welcomed:):)

---

### Post by a fenderson on 2007-10-11
open a terminal
'sudo aptitude install openoffice.org evolution'

---

### Post by thirddeep on 2007-10-11
Here you go:
```
sudo apt-cache search open | grep office
sudo apt-get install openoffice.org
```

Same deal for any other package.

Thd.

---

### Post by tomerl on 2007-10-11
thanks for the quick replies!

i've already tried "sudo aptitude install evolution", 
the problem is that when i've uninstalled it, it removed also evolution-plugin and evolution-exchange, 
however when i've run sudo aptitude install evolution it also wanted to install 30 more others as well...while synaptic doesn't do that.
so it's a bit confusing...as for open office, it goes the same, synaptic don't require all the other aps\libs while apt-get and apptitude does..

---

### Post by tomerl on 2007-10-12
anyone can help me with this?

---

### Post by a fenderson on 2007-10-12
The only thing I can think of is that you might have to tell aptitude not to install 'Recommended' packages automatically.  Open a terminal and type 'sudo aptitude'.  Press F10 to open the menu, move over to 'Options', and move down to 'Dependency handling'.  Uncheck the option that says 'Install Recommended packages automatically' and press enter.

---

### Post by tomerl on 2007-10-14
pressing F10 in terminal open up the file menu...

---

