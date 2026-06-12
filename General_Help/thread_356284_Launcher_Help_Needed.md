---
title: "Launcher Help Needed"
date: 2007-02-08
forum: General Help
---

### Post by banditti on 2007-02-08
I thought I had this figured out, but I am missing something.

This is what I have tried:

gksudo gnome-terminal -e /usr/bin/sim/runsim.sh


I have tried as many variants as I can think of with no avail. 

Thoughts?

---

### Post by sdide on 2007-02-08
Hey,

the shell you open sort of catches the exit of the program you run in it, with -e option.

so, if you do:

g```
nome-terminal -e "ls" 
```

you see nothing, but a windows momentarily open and closing.

if you do a 

```
gnome-terminal -e "sleep 5"
```

you should have a window pop up for 5 seconds and then shut down.

What I suggest is, that you just do:

```
sudo /usr/bin/sim/runsim.sh 
```

to run your program.

---

### Post by banditti on 2007-02-08
Thank you for your feedback.  However, that didn't work.

If I run ./usr/bin/sim/runsim.sh from a open term window, it works, can't get the launcher to work.

---

### Post by banditti on 2007-02-08
can I get a bump?

---

### Post by banditti on 2007-02-09
Lookin' for some love on this.

---

### Post by banditti on 2007-02-10
Still lookin' pa nub

---

### Post by sdide on 2007-02-11
Hey again, 

I can't quite figure it with gnome-terminal, 
but with xterm I can get the session not to terminate 
xterm has either the "-hold" option, that keeps the session alive untill you kill it.
or you can use a construct like

```
$ xterm -e "./test.sh > out.txt ; tail -f out.txt"
```

( i can't get this to work with gnome-terminal either.)
that way you the session doesn't close (tail -f never terminates) 
you get standard output in the file out.txt, and also to terminal.
where test.sh is the script you want to run..

Regards.

---

### Post by mcduck on 2007-02-11
> **banditti said:**
> Thank you for your feedback.  However, that didn't work.

If I run ./usr/bin/sim/runsim.sh from a open term window, it works, can't get the launcher to work.

When you do create the launcher set the type to 'Application in Terminal' instead of 'Application'.

---

### Post by banditti on 2007-02-12
Thank you both, mcduck, tried and no luck.

On a side note, it is always the simple things that get me.

---

### Post by mcduck on 2007-02-13
Well, this one at least should work. Create a script with 'gksudo gnome-terminal /usr/bin/sim/runsim.sh', and then point the launcher to that script.

That's how I'm starting ncmpc in gnome terminal with a panel launcher.

---

