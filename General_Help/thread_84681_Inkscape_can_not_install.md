---
title: "Inkscape can not install"
date: 2005-10-31
forum: General Help
---

### Post by majikstreet on 2005-10-31
Hey all,
I was trying to install inkscape (sudo apt-get install inkscape) and apt spat out this ever so friendly error:

[quote=Apt-Get Evilness]
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  inkscape: Depends: libgc1 but it is not installable
            Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not installable
            Depends: libgtkmm-2.4-1 but it is not installable
            Depends: libsigc++-2.0-0 (>= 2.0.2) but it is not installable
E: Broken packages
[/quote]

Thanks in advance,
majikstreet

---

### Post by Makrie on 2005-11-01
hey!

I used synaptic to attempt the install a couple of days ago and got an error which I recall as being close to that one...

just tried the install today (using synaptic with universe and multiverse enabled, FWIW) and it worked!

hope this helps in some way...

cheers

Makrie

edited to clarify timeline!

---

### Post by Makrie on 2005-11-01
oops... just remembered that at the time of my unsuccessful first install my dns settings were causing problems. they were automatically resetting to a default value every 15 minutes or so - **or whenever I tried to use synaptic**!

this meant that I would lose network connectivity and so nothing could be found. the problem seems a common one and I found a fix for it on the forum - happy to look it up again if you want.

in brief - I fixed my dns issues, enabled multiverse and universe support and it worked for me!

cheers

---

### Post by majikstreet on 2005-11-01
I don't think its that....

still can't install.

---

### Post by temcat on 2005-11-01
[QUOTE=majikstreet]I don't think its that....

still can't install.[/QUOTE]

Ubuntu developers won't like my advice, but install linux autopackage (.package file) from Inkscape website. Installed fine for me. Be sure not to install Ubuntu version of Inkscape on top of this afterwards! Best of all, install to your home directory (Autopackage allows this).

---

