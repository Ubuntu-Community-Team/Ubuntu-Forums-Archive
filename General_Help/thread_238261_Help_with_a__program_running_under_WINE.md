---
title: "Help with a  program running under WINE"
date: 2006-08-17
forum: General Help
---

### Post by insane_alien on 2006-08-17
i play around with Orbiter([www.orbitersim.com](www.orbitersim.com)) every now and again and i would like to get it on ubuntu so i can reduce my XP time.

it almost runs fine with wine. i can load up the program but it doesn't display scenario files (.sce) or modules (.dll). i know that this is a one off program and there is unlikely going to be anybody who can help, but, has anybody came across this sort of problem before? and can it be fixed?

---

### Post by hollaburoo on 2006-08-18
First try running it from the terminal (wine programname), and you should get some errors printed out on whats going wrong.  Anything thats says fixme:name, is the name of a dllthat isn't working, so try using native window dlls, which you can get by googling thier name.

---

### Post by insane_alien on 2006-08-18
I don't get any fixme: errors. the program does launch fine. its just that i should get a box with a list of scenarios in it. but that box is empty. there is also a tab that should dhow several plug ins which are .dll files and they too do not show up.

---

### Post by hollaburoo on 2006-08-18
try copying all dlls that come with the program to wine System32 folder.

---

### Post by insane_alien on 2006-08-19
Ok, i got it thanks to a little help from some other people using the program.i had to change directories to the parent directory and start it using the command line.

hollaburoo, that wouldn't work since the need to be in the modules folder. it uses a relative folder structure or something like that. i'm not a programmer so i didn't really catch all of what was said.

---

