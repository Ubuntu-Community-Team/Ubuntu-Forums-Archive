---
title: "Whats the default download file for firefox on gutsy Gibben"
date: 2008-01-18
forum: General Help
---

### Post by Lord Xeb on 2008-01-18
when you first get Gutsy Gibbon, what is the default file that .rpm go to in when downloaded through firefox

---

### Post by p_quarles on 2008-01-18
~/Desktop

---

### Post by zvacet on 2008-01-19
Ubuntu use deb file,not rpm.What are you trying to install?

---

### Post by Lord Xeb on 2008-01-19
Firestarter..... Finding a download that isn't a bunch of freakin' pieces is turning into a pain in the ***

---

### Post by Steveway on 2008-01-19
sudo apt-get install firestarter
This will install firestarter for you.
But why do you want it? Do you run a server? Otherwise it is not needed for a Desktop-user.

---

### Post by sub2007 on 2008-01-19
Yeah a .rpm won't run at all in Ubuntu (except if you convert it to a .deb using Alien but you may run into dependency issues). 

Firestarter is included in Ubuntu's repositories, to install it all you have to do is open a terminal and enter

**sudo apt-get install firestarter**

and it will install the program for you. 

You can also use the Synaptic Package Manager to install it (just do a search for Firestarter, mark it for installation and click Apply).

This is some useful reading: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

