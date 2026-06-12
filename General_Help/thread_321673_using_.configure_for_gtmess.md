---
title: "using ./configure for gtmess"
date: 2006-12-19
forum: General Help
---

### Post by PetePete on 2006-12-19
been trying to install gtmess, but everytime i run ./configure i get an error:

checking for pthread_create in -lpthread... yes
checking for library containing initscr... no
configure: error: cannot find curses library


i've got the ncurses library installed (in /lib) i think the problem is the ./configure script isn't looking in the right place. I've tried to specify the location but not sure if i've used the correct command, so could someone tell me how id tell it to look in /lib

anyone else got gtmess to work in ubuntu ?

---

### Post by jrib on 2006-12-19
do you have the -dev packages for curses? (libncurses5-dev on edgy)

---

