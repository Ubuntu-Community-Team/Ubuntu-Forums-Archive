---
title: "What's the terminal command for Crossover?"
date: 2007-02-22
forum: General Help
---

### Post by zami on 2007-02-22
What is the command to launch something with Crossover, from the terminal?

As in, if I'm launching something with Wine its "wine whatever.exe".  So with crossover its "____ whatever.exe". 

If I right click on something it offers to "Launch with Crossover", and of course I can go through the Crossover control panel, but I really want to see why I'm having problems with a certain program, and I'm hoping the terminal output can help me nail it down.

Thanks!

-zami

---

### Post by nereid on 2007-02-26
Wouldn't that be simply *crossover*?

---

### Post by Rippey on 2007-02-26
try the following:
"locate cxstart"
cd to the folder cxstart is in (you'll need to do this everytime you want to execute cxstart)
"./cxstart --help" shows all options

---

