---
title: "What is the process 'wish'?"
date: 2007-05-30
forum: General Help
---

### Post by xundaman on 2007-05-30
I tried searching everywhere, but to name a process with a verb is so genius that everything else appears except what I'm looking for. Anyone knows what is it about? It's eating a lot of memory here... It only says 'wish'.

Thanks in advance!

---

### Post by loathsome on 2007-05-30
**[COLOR="DarkSlateGray"]$ man wish[/COLOR]**

> DESCRIPTION
       Wish is a simple program consisting of the Tcl command language, the Tk
       toolkit,  and a main program that reads commands from standard input or
       from a file.  It creates a main window and then processes Tcl commands.
       If  wish  is  invoked  with no arguments, or with a first argument that
       starts with &#8216;&#8216;-&#8217;&#8217;, then it reads Tcl commands interactively from  stan&#8208;
       dard  input.   It  will  continue processing commands until all windows
       have been deleted or until end-of-file is reached  on  standard  input.
       If  there exists a file .wishrc in the home directory of the user, wish
       evaluates the file as a Tcl script just before reading the  first  com&#8208;
       mand from standard input.


---

### Post by blacksadness on 2007-05-30
> **xundaman said:**
> I tried searching everywhere, but to name a process with a verb is so genius that everything else appears except what I'm looking for. Anyone knows what is it about? It's eating a lot of memory here... It only says 'wish'.

Thanks in advance!

probably you have amsn running for some program using tk, killall -9 wish.. though it would be better to find which program is running using it

---

