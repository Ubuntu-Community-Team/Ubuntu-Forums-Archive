---
title: "GUI Package Management"
date: 2008-01-13
forum: General Help
---

### Post by Thund3rstruck on 2008-01-13
I'm brushing up on my C programming and I want to work on an Add/Remove Programs utility that will do the following:

1. Display a listview populated with all the applications installed on the machine
2. Allow the user to remove the selected installed package(s)
3. Query the selected package(s) to determine dependencies & installation paths
4. Interact with aptitude to allow for installation/re-installation of packages

Of course Synaptic allows for installing/searching packages but does it, or any other gtk utility, provide the above features?

If not, then I want to create this utility but if it does then of course I do not want to re-invent the wheel

---

### Post by SOULRiDER on 2008-01-13
AFAIK Synaptic can do everything aptitude can.

[quote]1. Display a listview populated with all the applications installed on the machine
2. Allow the user to remove the selected installed package(s)
3. Query the selected package(s) to determine dependencies & installation paths
4. Interact with aptitude to allow for installation/re-installation of packages[/quote

1: Check
2: Check
3: Deps yes, install path, not sure,
4: I believe it uses apt-get but not aptitude.

---

### Post by Thund3rstruck on 2008-01-13
> 
1. Display a listview populated with all the applications installed on the machine


Where in Synaptic can I get a list of the packages installed on my machine? I don't want to have to browse dozens of categories and filter through hundreds of packages that are not installed, just a clean UI like Windows Add/Remove Applet to display the applications currently installed (not separated by categories). 

Am I missing something? You are talking about the Synaptic program that ships with Ubuntu?

---

### Post by oldos2er on 2008-01-13
Yes, Synaptic does all those things. To see a list of all your installed packages, select 'Status' in the bottom right corner, then 'Installed. To see a package's dependencies, right-click on it, choose 'Properties,' 'Dependencies.' 'Installed Files' will tell you the location of each file in the installed package.

---

### Post by Thund3rstruck on 2008-01-13
Ah... ha... ok. 

Guess I need a new project :)

---

