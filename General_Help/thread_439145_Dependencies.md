---
title: "Dependencies"
date: 2007-05-10
forum: General Help
---

### Post by posiedon321 on 2007-05-10
I went to packages.ubuntu.com and went to dowload some packages for my installation and it listed several "dependencies." Can anyone tell me what a dependency is and are they required for installation?

---

### Post by taurus on 2007-05-10
What packages are you trying to install by hand?

---

### Post by useResa on 2007-05-10
> **posiedon321 said:**
> I went to packages.ubuntu.com and went to dowload some packages for my installation and it listed several "dependencies." Can anyone tell me what a dependency is and are they required for installation?A dependency is a relationship between packages.

 The package system has a range of package "dependencies" which are designed to indicate (in a single flag) the level at which Program A can operate independently of the existence of Program B on a given system: 
 [LIST]
[*]  Package A *depends* on Package B if B absolutely must be installed in order to run A.  In some cases, A depends not only on B, but on a version of B. In this case, the version dependency is usually a lower limit, in the sense that A depends on any version of B more recent than some specified version. 
[/LIST] [LIST]
[*]  Package A *recommends* Package B, if the package maintainer judges that most users would not want A without also having the functionality provided by B. 
[/LIST] [LIST]
[*]  Package A *suggests* Package B if B contains files that are related to (and usually enhance) the functionality of A. 
[/LIST] [LIST]
[*]  Package A *conflicts* with Package B when A will not operate if B is installed on the system.  Most often, conflicts are cases where A contains files which are an improvement over those in B.  "Conflicts" are often combined with "replaces". 
[/LIST] [LIST]
[*]  Package A *replaces* Package B when files installed by B are removed and (in some cases) over-written by files in A. 
[/LIST] [LIST]
[*]  Package A *provides* Package B when all of the files and functionality of B are incorporated into A.  This mechanism provides a way for users with constrained disk space to get only that part of package A which they really need. 
[/LIST]
Source: [http://www.debian.org/doc/FAQ/ch-pkg_basics#s-depends](http://www.debian.org/doc/FAQ/ch-pkg_basics#s-depends)

I hope this somewhat clarifies the term.

---

### Post by zvacet on 2007-05-10
Yes they are required because without them you can not run program.Download all you need for specific package and install dependencies first.

---

### Post by posiedon321 on 2007-05-10
I'm trying to install packages for software development and also xmms. But everytime I try to install one it tells me I have their dependencies installed. When I go to packages.ubuntu.com and download them, I get a bigger and bigger list of required packages. I'm still trying to figure out what packages are already install at the time of a clean install.

---

### Post by taurus on 2007-05-10
Is your Ubuntu machine not connected to the net right now?

---

### Post by zvacet on 2007-05-10
```
sudo aptitude install file_name
```

This will install package and all dependencies wich goes with it.If you still want to install from packages.ubuntu.com you can open synaptic and copy/paste every dependecy in search box to see if you allready have it installed.

---

### Post by posiedon321 on 2007-05-11
No, the internet is not available on the system in question. I must to the library and do the download the packages and install them by hand.

---

### Post by sdrawkcab on 2007-12-23
Ok, I've been trying to figure what the heck is going on for hours now. 

I just want to play the newest version of Scorched 3D on Gutsy Gibbon. The repos does not have the newest version as was stated above. I have the source code for the newest version, and have been trying to get the dependencies that were stated in the "COMPILE" folder within the source. I searched synaptic package manager and did not find many of them. I just did the "sudo aptitude" command and it downloads the version 40.1 stuff! This is driving me crazy.

---

### Post by zvacet on 2007-12-24
@**posiedon321**

If you don´t have internet on that comp try from some other using [this](http://www.nonetdebs.homeip.net/).

---

