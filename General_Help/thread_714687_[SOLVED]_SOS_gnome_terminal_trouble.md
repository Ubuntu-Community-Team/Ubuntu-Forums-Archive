---
title: "[SOLVED] SOS: gnome terminal trouble"
date: 2008-03-04
forum: General Help
---

### Post by mimicri8 on 2008-03-04
i always get this prompt when accessing the gnome terminal:
there was a problem for the command for this terminal: Text was empty (or contained only white spaces)

but then i can still practice scripting when i use ctrl+alt+Fn...


i am a linux newbie,,,ubuntu masters rescue me

---

### Post by erginemr on 2008-03-04
Are you sure that you are not using the same color for both the text and the background? You 
can check it with:
Gnome Terminal Menu -> Edit -> Current Profile... -> Colors Tab

Select a different color profile to see if it helps.

Also, can you please take a screenshot (PrintScreen or Alt+PrintScreen) of your gnome-terminal and attach your screenshot here?

---

### Post by mimicri8 on 2008-03-05
no, the colors are different, my boss here told me to re-install the terminal, so i did..and now it works!...thanks to you too

---

### Post by erginemr on 2008-03-05
Great then! 

And it is amazing that you have been using Ubuntu in the office, which is wonderful news. Now, back to work! :D

As a quick reminder:
**To close a thread **-> Select **"mark this thread as solved"** from the thread tools menu. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by dr.pythagora on 2008-03-12
Hi,

I do have the same problem: the gnome-terminal is empty, I cannot type any command, and I get the following error message:

There was a problem for the command for this terminal: Text was empty (or contained only white spaces)

I have tried to reinstall these packages:
gnome-terminal, metacity,
but no any solution, so far. Ubuntu gurus, please any solution.

pythagora

---

### Post by dr.pythagora on 2008-03-12
Hi,

I do have the same problem: the gnome-terminal is empty, I cannot type any command, and I get the following error message:

There was a problem for the command for this terminal: Text was empty (or contained only white spaces)

I have tried to reinstall these packages:
gnome-terminal, metacity,
but no any solution, so far. Ubuntu gurus, please any solution.

pythagora

---

### Post by dr.pythagora on 2008-03-13
I have solved the problem in a very easy way. I simply run the command

          gnome-terminal --command=bash

instead of simply

          gnome-terminal

It opens the gnome terminal with the bash prompt, as it should.

pythagora

---

