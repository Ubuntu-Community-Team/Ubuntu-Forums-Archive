---
title: "compiling R-2.0.1"
date: 2004-11-29
forum: General Help
---

### Post by drunken-wallaby on 2004-11-29
Hi there. For several reasons I have to use the current version of [**R**](http://www.r-project.org). I downloaded the tar-file, extracted it and ran ```
./configure
``` after I installed the necessary build-tools as suggested in the howtos. However, when I run the configure-script, I run into the following error I dont't know how to solve. ```
checking for Fortran libraries of f77...
checking for dummy main to link with Fortran libraries... none
checking for Fortran name-mangling scheme... lower case, underscore, extra underscore
checking whether f77 appends underscores to external names... yes
checking whether mixed C/Fortran code can be run... yes
checking whether f77 and gcc agree on int and double... configure: WARNING: f77 and gcc disagree on int and double
``` I'd be very happy, if somebody has a hint for me how to solve this problem between the c++ and fortran compiler :) thanks a lot for your help...

---

### Post by drunken-wallaby on 2004-12-27
Sorry for bumping this Topic but I can't work this problem out. Has anybody realized this problem too? I'd be very glad if this problem could be solved. Thanks a lot and sorry for bumping again...

Greets,
Bernhard

---

### Post by Thomasimov on 2005-06-02
Hi,
I experienced exactly the same problem... Since I didn't know how to configure Fortran compiler in a better way, I decided to override the problem ;-) by installing g77. Compiling R will then use this one before f77 (with whom there is this problem of int / double), and this works well !
Hope this helps...

Have fun with R !

---

### Post by drunken-wallaby on 2005-06-03
[QUOTE=Thomasimov]Hi,
I experienced exactly the same problem... Since I didn't know how to configure Fortran compiler in a better way, I decided to override the problem ;-) by installing g77. Compiling R will then use this one before f77 (with whom there is this problem of int / double), and this works well !
Hope this helps...

Have fun with R ![/QUOTE]

Thanks for answering. That's exactly how I solved the problem too. Unfortunately I forgot to post the solution to this thread, my fault...

---

### Post by trickard on 2005-06-10
Hello all,

I am a research scientist exploring a move from windows to linux.  I am a complete newbie with linux but have installed Ubuntu and started to explore it.  So far I really like this OS.  Its just a matter of getting everything I need working.

It is important that I get R installed.  Is it possible to just use apt-get to install the Debian version of R on ubuntu?  If so, will it take care of any dependencies?

Also it does not appear that either g77 or gcc are installed with the base ubuntu system, is that correct?


Thanks ahead of time for your help,

Cheers,
Tim

---

### Post by trickard on 2005-06-10
nevermind.  I tried apt-get and so far it appears to work.  

Tim

---

### Post by Kasanax on 2005-12-19
I'm a complete Newbie to Linux, so please bear with me...

I need a MiniTab-type program for my Stats class, so I tried installing R through Synaptic - I did a search for R (and naturally got lots of results), and I found "r-gnome."

I marked it for installation, and Synaptic automatically identified the other packages I needed to install. After okaying all the other packages, I hit apply. So, now I'm not sure if I actually installed R, and, if so, where to find it. :confused: 

I've been a Windows user all my life, and so this whole 'packages' thing is a bit complicated seeming... any help would be appricated! :D

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=Kasanax]I'm a complete Newbie to Linux, so please bear with me...

I need a MiniTab-type program for my Stats class, so I tried installing R through Synaptic - I did a search for R (and naturally got lots of results), and I found "r-gnome."

I marked it for installation, and Synaptic automatically identified the other packages I needed to install. After okaying all the other packages, I hit apply. So, now I'm not sure if I actually installed R, and, if so, where to find it. :confused: 

I've been a Windows user all my life, and so this whole 'packages' thing is a bit complicated seeming... any help would be appricated! :D[/QUOTE]
r-gnome is empty
search synaptic for r-
and install stuff that says "GNU R"
not everything but those you need.

---

