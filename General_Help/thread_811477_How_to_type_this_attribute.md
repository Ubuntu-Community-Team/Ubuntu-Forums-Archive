---
title: "How to type this attribute: |   ?"
date: 2008-05-29
forum: General Help
---

### Post by rado3105 on 2008-05-29
How to type this attribute: |   on keyboard? It is used in combination with grep, less. And what does it mean?

---

### Post by ad_267 on 2008-05-29
Everything you could ever want to know about it:
[http://en.wikipedia.org/wiki/Vertical_bar](http://en.wikipedia.org/wiki/Vertical_bar)

This section describes the use in Linux/Unix:
> Unix

A pipe is an inter-process communication mechanism originating in Unix which allows the output (standard out and, optionally, standard error) of one process to be used as input (standard in) to another. In this way, a series of commands can be "piped" together. This provides skilled practitioners the ability to quickly perform complex processing on the command line or as part of a UNIX shell script ("batch file"). In most Unix shells (command interpreters), this is represented by the vertical bar character.

e.g. Piped UNIX commands: egrep -i 'blair' filename.log | more

Traditionally, the piping capability in UNIX is provided by the "fork and exec" feature of UNIX operating systems. The UNIX shell forks off a copy of itself for each command, connecting the input of each to the output of the next. When processing large amounts of data, all processes in the pipeline will typically be active at the same time (within the limits of the hardware used). Using the UNIX pipe mechanism, a user is able to quickly and easily build a custom program composed of a (theoretically) unlimited number of small, specialized programs.

On my keyboard it's above the Enter and Below the Backspace on the same key as the backslash, so you have to press shift and backslash.

---

### Post by CameO73 on 2008-05-29
I wonder how you got that pipe-sign in your first post? ;) Anyway, I have to hold Shift and the \-key (left of the Enter-key) to get the pipe.

---

### Post by rado3105 on 2008-06-05
Thank you very much

---

