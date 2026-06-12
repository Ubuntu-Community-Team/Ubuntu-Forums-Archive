---
title: "How to tar-e some of the files"
date: 2020-08-28
forum: General Help
---

### Post by norbisan on 2020-08-28
I have files xd100000 to xd999999
I need to tar and bzip files files with name start xd10 contain numbers 38-101 and finish with 898
I need to do it in comand line  (bash)
How to do it ???
Best regards
Norbert

---

### Post by sisco311 on 2020-08-28
Hi, norbisan!

Is this your homework? What did you try?

I'm not sure if I understand which files do you have to archive. Could you elaborate your question?

What I think I understand is that the file name must begin with xd10 and must end with 898, but I'm unsure what do you mean by "contain numbers 38-101".

---

### Post by norbisan on 2020-08-28
Hi.
files have to start with xd10 then 38, 39, 40 .... 101 and end  with 898

other way xd10{38..101}898
It was some kind of task with i can not solve and can not find solution.
My idea was to use
ls xd10{38...101}898 | xargs tar -cvf files.tar {}
or
tar -cvf files.tar xd00000{11...15}898

---

### Post by sisco311 on 2020-08-28
Here is a hint.

You have an 8 character string and you know for sure 7 of them.  

Try to figure out which is the unknown and how is related to the others.

The bash part is trivial :)

---

### Post by norbisan on 2020-08-28
Hi,
that was only example.
The key question is about 38-101, or totally different range 1-999
but i found solution. It was in front of me 
tar -cvf files.tar xd00000{11..15}898
(Previous i had 3 dots and the solution are 2 dots)
Best regards

---

### Post by sisco311 on 2020-08-29
Please don't play with our time. 

We are here to help .Please don't ask XY questions:  [https://mywiki.wooledge.org/XyProblem](https://mywiki.wooledge.org/XyProblem)

---

