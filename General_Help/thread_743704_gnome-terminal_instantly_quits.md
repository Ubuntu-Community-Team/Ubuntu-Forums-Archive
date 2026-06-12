---
title: "gnome-terminal instantly quits"
date: 2008-04-02
forum: General Help
---

### Post by davidcaiazzo on 2008-04-02
Put simply when I click on my terminal icon the terminal seems like it is going to load then it just quits. I did ctrl+f2 and typed gnome-terminal same thing. I tried reinstalling it with synaptic but the problem persists does anybody have a solution?

---

### Post by davidcaiazzo on 2008-04-02
The plot thickens, I started up xterm and typed in gnome-terminal all I get is Bus error(core dump)

---

### Post by ibuclaw on 2008-04-02
The words **core dumped** are usually the final words of an app that is either incompatible, or tries to executable a command incompatible with your system.

ie:
the program was trying to access a memory location outside its address space.  The computer detected this problem and sent a signal to your program, which caused it to abort.


I'm not sure if you are familiar with any programming languages, but one such example is when you try to pass a piece of data to a variable without the operand **&** in C. You get:
```
 Segmentation Fault (core dumped) 
```

Some questions I can ask that may help me understand your problem better are:

Did gnome-terminal work on your LiveCD?
Has it worked before in the past?
Have you tried to run it in debug mode?
Have you sent a bug report to Launchpad about it?

Regards
Iain

---

### Post by davidcaiazzo on 2008-04-02
I know c++ and am learning python, but that is besides the point. Yes it did work in the past and on the live cd(if I remember correctly). I just reinstalled libc6 and gnome-terminal is working again, however for whatever reason the line spacing in it is all messed up.

---

### Post by ibuclaw on 2008-04-02
Cools.

You could try re-installing all of the other dependancies, if libc6 worked, perhaps one of the others will...

Regards
Iain

---

### Post by davidcaiazzo on 2008-04-03
Figured out the spacing problem, seemed that the font package that I installed using automatix tangled things up, this is probably due to the fact that I recently installed ubuntu-restricted-extras package which also as the msfttcorefonts aswell. Anyway got rid of the package, restarted gdm and voila all good. Tinivole thank you so much for your responses.

---

