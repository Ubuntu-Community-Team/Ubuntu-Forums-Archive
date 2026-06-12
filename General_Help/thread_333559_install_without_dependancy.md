---
title: "install without dependancy"
date: 2007-01-07
forum: General Help
---

### Post by nix4me on 2007-01-07
Hi,

I am trying to install the package devede from the repositories.  It has mplayer as a dependancy.  Probelm is, i compile my own mplayer package and it is already installed.  Synaptic and apt want to install the mplayer from the repository and I can't figure out how to make it no happen.

Is there a way for me to install devede without the mplayer package?

nix4me

---

### Post by koenn on 2007-01-07
you need to tell apt (the package manager) that mplayer is already installed (because you compiled it) - that way, it will know that the dependency to mplayer is satisfied. 

I believe the 'equivs'  tools can be used for that. you'll need to install package equivs 
and read this : [http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-helpers.en.html)

---

### Post by nix4me on 2007-01-07
Excellent!  It worked perfectly.

Thanks,

nix4me

---

### Post by koenn on 2007-01-07
y're welcome.

---

