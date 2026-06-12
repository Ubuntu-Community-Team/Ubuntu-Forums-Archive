---
title: "Can't install programs (Kubuntu)"
date: 2007-07-28
forum: General Help
---

### Post by grapeape25 on 2007-07-28
I'm trying to install certain programs that I want but I keep getting dependency errors.I've tried both "sudo apt-get install bluefish" and using the Adept Installer (GUI interface). Both of which just give me problems with dependencies. 

sudo apt-get install bluefish gives me

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bluefish: Depends: libgnomeui-0 (>= 2.13.0) but it is not going to be installed
E: Broken packages


I don't see why bluefish wouldn't work, I have installed it on KDE (on other distros) berfore. Also, isn't it supposed to download all the dependencies automatically?

---

### Post by wsmoser2004 on 2007-07-28
I think once upon a time I had a problem like this, and I fixed it with "sudo apt-get -f install".  In this case, -f means something like "fix dependencies," not "force" like in other programs.  And I think you do not put a program name after 'install,' although I could be wrong about that so try it both ways.

---

