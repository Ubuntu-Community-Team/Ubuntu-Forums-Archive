---
title: "How to update Kernel from 2.6.20-15 to 2.6.20-16 with Synaptic?"
date: 2007-06-05
forum: General Help
---

### Post by pjalegria on 2007-06-05
Hi

I want to no how can update Kernel from 2.6.20-15 to 2.6.20-16  with synaptic

Tank you

---

### Post by tomane on 2007-06-05
Hi,

I am assuming that you have the repositories configured and acessible through the network.
Just fire up synaptic, then click "Reload" to ensure that you have an up-to-date package list. Then click "mark all upgrades" and synaptic should mark your kernel package to be updated, as well as restricted modules and any other packages that have more recent versions in the repositories. This requires that you have the linux-generic metapackage installed, which is the case with a default instalation of *ubuntu.

cheers,
--to

---

### Post by pjalegria on 2007-06-05
Dont work...

Maybe the problem is this, i already have made the Kernel update, but i have problems and i have to return for the old kernel and i remove the new kernel with synaptics. Now i want to install again the new kernel.

How cant i do this?

---

### Post by tomane on 2007-06-05
Guessing from the kernel version, I supose you're using feisty/7.04, right?
Which message does it throw when it fails?

Choose "custom filters" on the left pane and then choose "broken" does it show anything?
I haven't tried forcind older package versions myself so I'm not much into it.
Can't you simply select the linux-image-2.6.20-16-generic package and mark it for instalation?
I'm just shooting in the dark, if you have any error messages thrown in the process, please post them and it will be easier for me and others to provide better advise.

boa sorte :-)
cheers,
--to

---

### Post by pjalegria on 2007-06-05
Solved...

P.S.- Porque estamos a falar Inglês?:D

Obrigado

---

