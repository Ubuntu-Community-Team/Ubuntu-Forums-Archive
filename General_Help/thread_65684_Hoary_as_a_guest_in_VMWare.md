---
title: "Hoary as a guest in VMWare"
date: 2005-09-14
forum: General Help
---

### Post by mlomker on 2005-09-14
I successfully installed Kubuntu Hoary into a VMWare session.  I'm running v5 Workstation on my amd64 Kubuntu system.  The goal is to have the 32-bit version in a VMWare session so that I can build packages and help answer questions for people on this forum.

Everything worked really well except for the keyboard.  If I try to type at more than about one character per second it acts as if the keyboard is stuck and I get a mess on every command line.  I've tried setting the xorg.conf config to match my primary install and I've looked into the kbdrate command-line tool with marginal success.  

Has anyone seen this before?  The problem might be unique to my laptop, but my XP VMWare session doesn't have any such issues.

---

### Post by Bil-E-daKid on 2005-09-14
Hey there,

I'm sure you will have already done this but, the only time I've seen problems like that is when the VMWare tools aren't installed in the VM.

Sorry I can't be any more help!

regards

---

### Post by mlomker on 2005-09-15
[QUOTE=Bil-E-daKid]I'm sure you will have already done this but, the only time I've seen problems like that is when the VMWare tools aren't installed in the VM.
[/QUOTE]

The tools don't do anything for the keyboard driver.  The first thing that I did was compile/install the tools and that went fine.  If you don't do that then you have to Ctrl-Alt every time you want your mouse to leave the window and that's uber-irritating!  lol.

---

### Post by mlomker on 2005-09-20
I upgraded to the beta version of VMWare 5.5 Workstation today and the problem seems to be resolved.  If you have the described problems in VMWare 5.0 then grab a copy of the newer version.

---

