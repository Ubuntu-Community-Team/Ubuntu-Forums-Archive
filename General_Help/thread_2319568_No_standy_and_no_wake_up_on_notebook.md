---
title: "No standy and no wake up on notebook"
date: 2016-04-05
forum: General Help
---

### Post by Hesediel on 2016-04-05
I have an HP 15 ac 191 nl

with:

Intel® Core™ i5-5200U with integrated Intel HD 5500 
RAM 8 gb
DEdicated GPU AMD Radeon R5 M330 

if i try t go in suspend mode the display became black but the fan stills going on. After that i cant wake up the pc, every key does not wok, i have to push the power botton for 3 sec for shut it down.

This problem is running with the 16.04 version but it was present also with the 15.10, ehat can be?

---

### Post by Hesediel on 2016-04-08
edit> i tried the live of 15.10 and i was remembering wrong, in this version the suspend mode works, tried also the 16.04beta2 in live version, same stuff of the post: freezes the pc

---

### Post by Hesediel on 2016-04-19
Np answers ut i figured out the problem. It seems to be a kernel problem.
Openeda bug on launchpad the y ask me to try the 4.6 kernel.

I tried the 4.5.1 and this kernel solved the problem. KErnel 4.5 does not.

Now i downloaded the deb kernel from the wiki site i was unable to install the deb of header due to dependences problem.

Now what do you suggest? Install the distro and then install at least manually the 4.5.1 kernel? In wich way i can install it?

---

