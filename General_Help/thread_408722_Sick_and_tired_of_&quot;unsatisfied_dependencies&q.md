---
title: "Sick and tired of &quot;unsatisfied dependencies&quot;"
date: 2007-04-13
forum: General Help
---

### Post by Ryupower on 2007-04-13
hey
I was searching online for some good open source audio and video editing programs, found debs from various projects, but not one interesting one installed. 

Why? Because it keeps on claiming that I have unsatisfied dependencies. I check in synamptec if I have this package installed, most of the time I do. 

so why is it giving me "unsatisfied dependencies" if I have them installed?!?!

Anyone willing to help, please do so.

I always get my hopes up finding some good editing program and the next thing I know is it gives me errors while compiling or while trying to install a .deb, saying that I am missing those dependencies.

---

### Post by HereInOz on 2007-04-13
it seems odd that you are getting unsatisfied dependencies if you already have that package installed.

Are you installing using sudo, or installing as user?  If you are installing as user, try sudo.  No promises - just a thought.

---

### Post by PurplePenguin on 2007-04-13
Sometimes it helps to install the "dev" package as well.  So if one of your dependencies is "example", install both "example" and "example-dev".

We're lucky with Ubuntu, though... there are thousands and thousands of great pieces of software available in the different repositories that will install with a click or two and no worries about dependencies.

---

### Post by kerry_s on 2007-04-13
Using debs outside of the repos is always going to be tricky. If you can find debs for debian stable it would be more inline with dapper, dappers programs are old in linux time. On top of that ubuntu has there own way of doing things that is not the standard debian way so you have to careful you don't conflict or it will toast your install.

The best thing to do would be to compile the programs to your current install. You can use check install to get a deb you can save.

---

### Post by handaxe on 2007-04-13
> **Ryupower said:**
> Why? Because it keeps on claiming that I have unsatisfied dependencies. I check in synamptec if I have this package installed, most of the time I do. 

Either there is something very wrong here or what you think is the right package is in fact not, differing in some perhaps subtle aspect of the name or version. Short of a corrupt apt, I would think the second.

I too have been frustrated when hopeful... Compiling is your friend then..

HA

---

### Post by az on 2007-04-13
Forget about binary compatibility.

Windows is binary-compatible.  The binary version (the executable version) of an application build and distributed for windows 98 will run on windows vista.  This is not so in the linux world.

Keeping a stable binary interface for applications comes in second to keeping an easy path for colaborative development.  The software is excellent because of that.

A binary package build for another debian-type ditro will not work on a different debian-type distro.

---

### Post by justin whitaker on 2007-04-13
> **Ryupower said:**
> hey
I was searching online for some good open source audio and video editing programs, found debs from various projects, but not one interesting one installed. 

Why? Because it keeps on claiming that I have unsatisfied dependencies. I check in synamptec if I have this package installed, most of the time I do. 

so why is it giving me "unsatisfied dependencies" if I have them installed?!?!

Anyone willing to help, please do so.

I always get my hopes up finding some good editing program and the next thing I know is it gives me errors while compiling or while trying to install a .deb, saying that I am missing those dependencies.

Ryu, first, what are you trying to install? Next, maybe you should uninstall all the apps that you have, and use aptitude or synaptic to reinstall them. Also, have you looked at the Ubuntu Studio project?

---

