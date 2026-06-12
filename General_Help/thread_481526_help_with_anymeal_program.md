---
title: "help with anymeal program"
date: 2007-06-22
forum: General Help
---

### Post by ronbrooks on 2007-06-22
Has anyone gotten anymeal to work with Ubuntu 7.04.  I have tried to set up a data base but each time i get an message that will pop up and say Directory '/home/ronbrooks/.kde/share/apps/anymeal/db' does not exist. Should the database be created? So I click make the director and then I get a message Failed to create directory '/home/ronbrooks/.kde/share/apps/anymeal/db': Is a directory.  Does anyone have any idea as to how to fix this so the program will work.

---

### Post by MozartlovesUbun2 on 2007-11-13
um ok how does this thing work on gutsy, i'm hungery :)

---

### Post by liopia on 2007-11-23
I have the same problem as Ron. Any help would be greatly appreciated.
installed using apt-get

7.10
Fluxbox

anymeal -v:
Qt: 3.3.7
KDE: 3.5.8
AnyMeal: 0.30

---

### Post by aaronhelton on 2007-12-19
There are two database options for AnyMeal on Ubuntu.  You can use the embedded one, which wants to create a MySQL socket in your home directory, or you can use Network, which will allow you to connect on localhost.  Of course, you should have MySQL installed and running before you try this, but this is what worked for me.  Hopefully that helps.

---

### Post by d3j4v00 on 2007-12-29
I am having the same issue on Ubuntu 7.10

Also, it keeps calling for KDE things I don't have installed.

Taking aaronhelton's advice, I'll be searching the forums now for how to get "MySQL installed and running."

---

