---
title: "How to remove broken pkg libstdc++6?"
date: 2007-10-17
forum: General Help
---

### Post by jmacak on 2007-10-17
Hi

I was hoping to install pdfedit on my feisty amd64 system and was following the instructions posted on an ubuntu forum that indicated that I first needed to install libstdc++6.  Well, the libstdc++6 install (using apt-get) failed  because of failed dependencies.  

Now when I go to apply updates, the updater wants do de-install about 350 packages.  If I run apt-get check I get:

 sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libstdc++6: Depends: gcc-4.2-base (= 4.2.2-3) but it is not installable
              Depends: libc6 (>= 2.6.1-1) but 2.5-0ubuntu14 is installed
              Depends: libgcc1 (>= 1:4.2.1) but 1:4.1.2-0ubuntu4 is installed
E: Unmet dependencies. Try using -f.


If I do as suggested (apt-get -f install) I am presented with:

.
.
.
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libstdc++6 (due to apt)
0 upgraded, 0 newly installed, 343 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1343MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.


Is there something I can do to clean this up?  Is there something I can do to tell apt to forget about installing the libstdc++6 package?

Thanks

---

### Post by zvacet on 2007-10-18
[http://packages.ubuntu.com/feisty/base/libstdc++6]("http://packages.ubuntu.com/feisty/base/libstdc++6")

 Download and install dependencies.

---

### Post by jmacak on 2007-10-18
Hi

OK, so you suggest that, rather than abandon the installation, I should try to make it complete.

I'll give that a try when I get back to the machine.

cheers

---

### Post by jmacak on 2007-10-19
Hi 

Thanks.

But, when I try to install anything, including those dependencies, apt still wants to get rid of those ~350 packages first.

Is there some way to get the system to just forget about finishing up the setup for that borked package?

Certainly this MUST be something that comes up occasionally, there should be a way to tell apt to just 'forget' about any pending operations.  

cheers

---

### Post by jmacak on 2007-10-20
Hi 

Thanks for all the help, I ended manually re-installing the packages to go back to version 4.1.2 of libstdc++6.  This included applying unmet dependencies (mainly rolling-back versions) as needed.

cheers

---

