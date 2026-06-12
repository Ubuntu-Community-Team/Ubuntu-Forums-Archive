---
title: "geda schematic editor won't start"
date: 2005-10-27
forum: General Help
---

### Post by NRios on 2005-10-27
I have installed geda and all suggested packages using synaptic, with no errors. It launches OK from a console, and I can create a new project and add a new file to it of the schematic kind.

However, when I try to edit that schematic and gschem is called, it fails to start after printing the messages quoted below in the console; what can it be?

Thanks,

[INDENT].NRios.[/INDENT]

[INDENT][FONT="Courier New"]gEDA/gschem version 20040111
gEDA/gschem comes with ABSOLUTELY NO WARRANTY; see COPYING for more details.
This is free software, and you are welcome to redistribute it under certain
conditions; please see the COPYING file for more details.
Error : system-error [C:52 L:25] in /etc/gEDA/system-gschemrc
Most recently read form: (#@load (#@string-append #@gedadatarc /system-commonrc))
Failed to read init scm file [(null)/gschem.scm]
[/FONT][/INDENT]

---

### Post by FJ_Sanchez on 2005-10-27
I have the same problem... today I installed with aptitude geda and geda-utils packages from universe repository but I cannot open gschem for example. I'm using breezy upgraded from hoary server installation on a x86 machine.

Any recomendations?

Thank you.

---

### Post by Kubiack on 2005-11-02
I have the same problem.
I have downloaded the image-CD version of gEDA in order to perform installation without the package manager.
The automatic installation script doesn't work, so i have tried to install manually all the packages,like describe in the "INSTALL.problem" text in image-CD. During the compilation, i have a lot of error message, it seems that i need an additionnal package; probably describing new C++ vartypes.

I haven't succeeded to install this soft :(

email me if you have find a solution

---

### Post by MeanRoy on 2005-11-17
Alright, I'll go back and see what I did.
I'm running it.
It didn't load itself into the menu system though, I had to go fish.
I thought I posted that in another thread.

---

### Post by daller on 2006-02-15
The gschem error has been reported here:

[https://launchpad.net/distros/ubuntu/+source/geda-gschem/+bug/4440](https://launchpad.net/distros/ubuntu/+source/geda-gschem/+bug/4440)

---

### Post by daller on 2006-02-16
My  crappy howto may solve the problem untill someone get the repo-version running.

[http://ubuntuforums.org/showthread.php?p=742110#post742110](http://ubuntuforums.org/showthread.php?p=742110#post742110)

---

### Post by Ex-Cyber on 2006-02-17
The problem is that the package is missing the 'system-commonrc' configuration file. This is a known bug in the Debian package and has been fixed in unstable (in fact, it was fixed quite a while ago, well before the Breezy release; it might be a good idea to find out why the updated package didn't make it in).

---

