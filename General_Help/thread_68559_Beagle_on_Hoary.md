---
title: "Beagle on Hoary?"
date: 2005-09-23
forum: General Help
---

### Post by Joey French on 2005-09-23
Man, I've been trying to get beagle installed, but it gives me crazy error messages. I've tried the HOWTO, Synaptic, various other ideas on the web, cannot get it installed. Anyone else have this problem?

Here we go:

Synaptic- 

 beagle:
 Depends: mono-jit but it is not going to be installed
 Depends: libgconf-cil but it is not going to be installed
 Depends: libglade-cil but it is not going to be installed
 Depends: libglib-cil but it is not going to be installed
 Depends: libgnome-cil but it is not going to be installed
 Depends: libgtk-cil but it is not going to be installed
 Depends: mono-assemblies-base but it is not going to be installed
 Depends: libgmime-cil but it is not going to be installed
 Depends: libevolution-cil but it is not going to be installed

So, I try to install the packages by hand, one by one...
Shell- 
joey@homebox:~$sudo apt-get install mono-jit
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mono-jit: Depends: mono-assemblies-base-1.1.7 but it is not installable
E: Broken packages
joey@homebox:~$   

What is the deal? I heard that beagle requires a kernel compiled for inotify, (I think it is) but on the beagle homepage, it says it is "not recommended". Maybe it will be in Breezy, I think I heard it is a feature, but don't remember it on the live disc. 

Anyone gotten beagle working on Hoary, am I overlooking something?
Thanks in Advance!
Joey

---

### Post by Joey French on 2005-09-28
Anyone?

---

