---
title: "Finding packages installed from a certain repository"
date: 2006-10-11
forum: General Help
---

### Post by .t. on 2006-10-11
Say I want to remove all packages that I had installed from a repository, what command would I use to discern the list of installed packages from that repo?

---

### Post by whizbaby on 2006-10-11
The only simple thing I can think of is:
open synaptic and define a new filter in the *settings* menu so that only packages you want to uninstall are shown.
Any other ideas?

---

### Post by .t. on 2006-10-11
Hmm... That doesn't really work, unless "Sections" are something special. What are they, and how are they used?

I was looking for something more terminal-based really, but I'll use a GUI if that's the only option.

---

### Post by whizbaby on 2006-10-11
I also prefer the terminal, but I really don't know how to (like you). I never used the synaptic filter before, but I juat created one and selected all the multiverse packages and checked 'only selected sections' (or similar). Now I can select it in 'custom' (button is somewhere at the lower left edge of the screen). I suppose you want to remove some other kind (e.g. plf or blutkind.org) of repository?
EDIT:
I'll keep on trying because the solution would be interesting.

---

### Post by whizbaby on 2006-10-11
State:
in
/var/lib/apt/lists
all package lists from the repositories are stored
so e.g.

grep Package: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages

results in

Package: desktopsecure
Package: opera
Package: realplay

one could remove the preceding 'Package:' and would have a package list. I'm currently looking how to put all this in a single command line producing the desired package list so it could be uninstalled with apt.

---

### Post by whizbaby on 2006-10-12
grep Package: /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages|cut -d : -f 2

gives the list

---

### Post by .t. on 2006-10-12
Thank you very much. I must learn grep and sed and cut and stuff properly...

---

