---
title: "Why I can't run ojects of c programs in ubuntu?"
date: 2015-08-22
forum: General Help
---

### Post by Avinash_Pandey on 2015-08-22
I am new to ubuntu as well as to programming. I made some c programs and their executable objects in one of the computers in computer lab of my college. I made these programs in Ubuntu (don't know which version) which was running as guest OS (windows 8.1 was the host OS). I then compressed the whole folder in .zip and uploaded it to One Drive.
Back at my room, I downloaded the zip file, extracted it, tried to run some objects using ./objectname command in the terminal and it throws some error. See the screenshot. However, I am able to open all the .c files using gedit command. I am also able to run the objects which were made on my laptop. I run ubuntu 15.06 64-bit with windows 8.1 as dual boot.
Why is this happening and how can I run those objects?
Please help me. Thank you.
[IMG]http://i60.tinypic.com/2egbok7.png[/IMG]

---

### Post by coldraven on 2015-08-22
Maybe you need to change the ownership of the folder.

---

### Post by smelheim85 on 2015-08-22
Could you provide your code please.  If you are going to be programming in a terminal you need tell the program how to execute itself.  If you are doing something like python, at the top you need.

#!/usr/bin/python

for perl

#!/usr/bin/perl.

I've never programmed in c before but I think it's "#!/bin/csh" but I could be wrong.  Another thing I don't know if it matter but for python at least you need to tell the compiler what version you are programming in.

#!/usr/bin/python3

---

### Post by mystics on 2015-08-22
Try running

```
file <executable name>
```

One  of the first things should be whether it is a 32 or 64 bit executable. Is that  different than what you're computer is? In other words, is it saying it  is a 32 bit executable while your computer is 64 bit (or vice versa)?

> **smelheim85 said:**
> I've never programmed in c before but I think it's "#!/bin/csh" but I could be wrong.  Another thing I don't know if it matter but for python at least you need to tell the compiler what version you are programming in.

Though used in Perl and sometimes in Python, this shouldn't be necessary for C.

---

