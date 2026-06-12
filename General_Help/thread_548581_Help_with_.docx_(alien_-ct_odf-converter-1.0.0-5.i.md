---
title: "Help with .docx (alien -ct odf-converter-1.0.0-5.i586.rpm?)"
date: 2007-09-11
forum: General Help
---

### Post by drawkcab on 2007-09-11
Hi.  I am a noob running Feisty on an amd64 and I need to be able to read .docx to stay working in Ubuntu.

As per the sticky, I have been following the instructions here:

[http://ubuntuforums.org/showthread.php?t=533564&highlight=.docx](http://ubuntuforums.org/showthread.php?t=533564&highlight=.docx)

and here:

[http://www.sigmundvoid.com/?p=81](http://www.sigmundvoid.com/?p=81)

------------------------------------------------------------------------------------------------

I've installed alien, seems to work just fine.  I've downloaded odf-converter-1.0.0-5.i586.rpm from the website as directed (to desktop).

When I try to run, 

alien -ct odf-converter-1.0.0-5.i586.rpm 
(also prefacing it with sudo or fakeroot)

I get:  

*File "odf-converter-1.0.0-5.i586.rpm" not found.*

I know I must be doing something stupid.  Any ideas?

---

### Post by arekmenner on 2007-09-20
> **drawkcab said:**
> When I try to run, 

alien -ct odf-converter-1.0.0-5.i586.rpm 
(also prefacing it with sudo or fakeroot)

I get:  

*File "odf-converter-1.0.0-5.i586.rpm" not found.*

I know I must be doing something stupid.  Any ideas?

There is a possibility that you are not in the right folder. Open the terminal (Applications >> Accessories >> Terminal)

Then, type cd Desktop and try the command again. (At any point you can type ls to see the files in the folder you are in)

---

### Post by drawkcab on 2007-11-22
I noticed this thread has been viewed 300 times.  Anyway, here is what worked for me on my latest install:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#OpenOffice_add_ons](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#OpenOffice_add_ons)

---

### Post by shafin on 2007-12-04
In gutsy, docx support is enabled by default,nothing like this is actually required,just right click a docx file and open it in OO

---

### Post by Rizado on 2007-12-05
> **shafin said:**
> In gutsy, docx support is enabled by default,nothing like this is actually required,just right click a docx file and open it in OOIt doesn't seem to be able to save however.

---

