---
title: "frotz errors - oss sound and curses"
date: 2007-10-07
forum: General Help
---

### Post by ed-koala on 2007-10-07
Hi, have not found any answers to this on web so hoping I can find an answer here.

I am trying to run Zork using frotz, but I'm getting two error messages. Here is what it says:

ed@ed-desktop:~/Desktop/Games/Zork1$ frotz -Z Zork1
FROTZ V2.43     oss sound driver, curses interface.
An interpreter for all Infocom and other Z-Machine games.
Complies with standard 1.0 of Graham Nelson's specification.

I checked Synaptic and my hardware.  My sound device supports oss.  I have a curses pkg loaded- evms-ncurses.

Anyone know what I should do to resolve these errors?  Thanks

---

### Post by ed-koala on 2007-10-07
Tried reinstalling frotz, still have same problem.

Can anyone recommend a different way to run the Zork Z-machine games?

---

### Post by jocko on 2007-10-07
> **ed-koala said:**
> ed@ed-desktop:~/Desktop/Games/Zork1$ frotz -Z Zork1
FROTZ V2.43     oss sound driver, curses interface.
An interpreter for all Infocom and other Z-Machine games.
Complies with standard 1.0 of Graham Nelson's specification.

Where's the error messages?
To me it looks like it simply informs you about the fact that it uses oss and curses, but it does not say that anything is wrong.
And I don't think that "evms-ncurses" is what you need.
That's just a program that uses the ncurses interface, it does not provide it.
More likely is that you need "libncurses5", but if you installed frotz from the repos, you should already have it, it is listed as a dependency for the frotz package.

---

