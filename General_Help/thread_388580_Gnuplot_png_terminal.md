---
title: "Gnuplot png terminal"
date: 2007-03-19
forum: General Help
---

### Post by irishScott on 2007-03-19
So I set up gnuplot 4.0 on Ubuntu 6.10 via Synaptic, and everything looks good until I try "set terminal png" I get

 unknown or ambiguous terminal type; type just 'set terminal' for a list


From what I can tell from google, I've got all of the necessary libraries installed, and I've tried reinstalling various versions of gnuplot via various methods (apt-get, tarball, pre-compiled, CVS, all with the same results)

I'd use another output format, but I need png specifically for an assignment.

Any suggestions?

---

### Post by irishScott on 2007-03-20
bump

---

### Post by JonathonReinhart on 2008-07-15
Hey, I come from a SuSE world, but I was having the same problem.  I went in to Yast and looked, and lo and behold, libgd-devel was not installed.  Install the devel package, reconfigure/compile and you should be good to go! sorry this is like a year late!


Jonathon

---

