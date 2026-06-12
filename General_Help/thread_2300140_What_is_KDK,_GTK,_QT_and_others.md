---
title: "What is KDK, GTK, QT and others?"
date: 2015-10-23
forum: General Help
---

### Post by michael-piziak on 2015-10-23
I come across these programs that have these initials in them or in their description - what to make of all this?  Like, will they all work in Ubuntu?

screenshot:

---

### Post by TheFu on 2015-10-23
Those are software libraries used to build the program. Knowing which is used is helpful to people with limited compute or RAM resources. Any programmer used to compiling and linking their own software would understand this.
There are wikipedia articles for the most popular libraries which may explain more details.

---

### Post by michael-piziak on 2015-10-23
> **TheFu said:**
> Those are software libraries used to build the program. Knowing which is used is helpful to people with limited compute or RAM resources. Any programmer used to compiling and linking their own software would understand this.
There are wikipedia articles for the most popular libraries which may explain more details.

ok thanks for the useful info.

& to my other question, are all these different software libraries able to be run by Ubuntu

12.04 lts here

---

### Post by TheFu on 2015-10-23
That answer is "it depends."  Sorry. 

If you always load software through the package manager, then dependencies like which libraries are used will almost always be handled so that you don't need to know.

When going outside the package manager to load software - you are telling the OS that YOU  know what you are doing (even if you don't) and accept responsibility for manually handling dependencies, compatibilities, and updates going forward. 

Almost always, loading any software outside the package manager is a bad idea. There are exceptions, but I try to use the versions already in the repos myself. BTW, I  worked as a cross-platform C/C++ developer for over a decade.  Package  management is one of the main reasons I prefer Linux over the commercial OS offerings.

Doesn't appear that the basic understanding of "libraries" has been captured.  Some light reading:
* [https://en.wikipedia.org/wiki/Library_%28computing%29](https://en.wikipedia.org/wiki/Library_%28computing%29)
* [https://en.wikipedia.org/wiki/Qt_%28software%29](https://en.wikipedia.org/wiki/Qt_%28software%29)
* [https://en.wikipedia.org/wiki/GTK%2B](https://en.wikipedia.org/wiki/GTK%2B)

---

### Post by michael-piziak on 2015-10-23
I know there is a synaptics package manager, but does the Ubuntu software center include what you mean by try to always use the package manager to get things.

On occasion, I can only get what I need using terminal - which is what you would say is outside package manager - ?

---

### Post by bab1 on 2015-10-23
> **michael-piziak said:**
> I know there is a synaptics package manager, but does the Ubuntu software center include what you mean by try to always use the package manager to get things.

On occasion, I can only get what I need using terminal - which is what you would say is outside package manager - ?
The package manager is APT.  Everything else you talked about are interfaces to APT.  Synaptics is a GUI front end and so is Ubuntu Software Center.  The terminal has 2 text based front ends to APT.  They are *aptitude* and *apt-get*.

Edit: installing a .deb package from the command line is not using the APT package manager.

---

### Post by SeijiSensei on 2015-10-23
Are you intending to write programs that would need these toolkits?  Otherwise you can just let the dependency management features in apt handle them for you.  For instance, most programs that run the in "K Desktop Environment (KDE)" are written to work with Qt libraries.  Many programs written for standard Ubuntu use the "Gnome Toolkit (GTK)."  Unless you're a programmer none of this matters.  If you were to install Gwenview, the graphics viewer native to KDE systems like Kubuntu, apt would pull in the needed Qt libraries as well.  If you install a program like Firefox on Kubuntu, you'll get the GTK libraries since Firefox uses those.  For example, if you have Firefox installed, run the command "dpkg -s firefox" to see the libraries it requires.  One of them is libgtk.  Running the same command for Gwenview lists libraries like libqtcore4 and libqtgui4.

---

