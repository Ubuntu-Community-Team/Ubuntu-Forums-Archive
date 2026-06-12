---
title: "Is there a compiler for fortran?"
date: 2005-05-13
forum: General Help
---

### Post by GAW-Snow on 2005-05-13
I've been using g++ for C++.  What do I use (and how do I get it) for fortran?

---

### Post by defkewl on 2005-05-13
I haven't been able to find one from the repositories. Perhaps you need to compile it yourself. The ones I know is GNU Fortran CMIIW.

---

### Post by az on 2005-05-13
It is called g77

apt-cache show g77

---

### Post by GAW-Snow on 2005-05-13
What about a compiler for fortran 90?

---

### Post by ssam on 2005-05-14
isnt FORTAN 95 a big new thing in GCC 4?

ps is this for scientific stuff? could you add any info you find to the [Ubuntu Scientists wiki page](http://www.ubuntulinux.org/wiki/UbuntuScientists)

---

### Post by GAW-Snow on 2005-05-14
I'm a physicist.  Thought I'd try out linux.  And yes, this is for scientific stuff.  I'm writing some programs for a research I'm doing.

Must admit, though, I feel like a student all over again.  It's always fun to learn new stuff.

By the way, I got it to work fine.  Looks like everything seems to be working perfectly.  Somebody gave me this older version of ubuntu.  I can see now that there is a newer version.  Is it worth the trouble to install the hoary version?

---

### Post by az on 2005-05-14
You just have to add the cd as a repository and do a smart upgrade and you will have the newest version.  You will not lose any data.

It should take about twenty minutes...

Actually, if you do not have the cd, just change your repositories to point to Hoary instead of Warty and do a smart updrade.  Same thing.  

Using Synaptic, edit each of your repositories and change the word Warty to hoary....

---

### Post by GAW-Snow on 2005-05-14
How do I add the cd as a repository and do the smart upgrade?

---

### Post by GAW-Snow on 2005-05-14
Never mind!  Done it.

---

### Post by phen on 2005-06-17
intel offers a free fortran95 compiler (for personal use only!). i use it for my studies. unfortunately, the software comes as rpm, so its a bit tricky to install.

i did not get it to work (downloaded it yesterday...), but collegues are using it under debian, so it should be no problem.

[http://www.intel.com/software/products/noncom/](http://www.intel.com/software/products/noncom/)

about the licence:

```
Welcome Linux* Application Developers<br>
Intel has expanded its offerings of free Linux tools for non-commercial software development. This offering is provided to developers who are developing software on their own time without compensation. Check FAQ for non-commercial definition and use.
```

we could stay in touch for installation help. at the moment, i have to set those paths, which should have been set by the installation script (that does not work because of the rpms....)

my steps were so far:

- downloading
- installing the rpm with alien -i  ("intel-ifort-8-8.1-386.rpm" for me)
- trying to set the variables with the script  "ifortvars.sh"


cheers,

kai

---

### Post by desdinova on 2005-06-17
On Debian and some other Linux's you have to add some extra steps to get it to work

I use a shell script called compile_fortran that looks like this

#/bin/sh
/opt/intel/compiler70/ia32/bin/ifcvars.sh
/opt/intel/compiler70/ia32/bin/ifc $1 -o $2 -i_dynamic

SO you call it like

compile_fortran source.f90 compiled_executable

(Doing an M.Phys in Astrophysics here ;-) )

---

### Post by Nekrataal on 2005-08-13
Anyone Knows how to get the Intel Fortran 9.0 to work on Ubuntu Hoary??, i get an error saying that it could not find the installation path for g++

---

