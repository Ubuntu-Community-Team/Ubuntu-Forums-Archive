---
title: "Re-install ubuntu"
date: 2008-03-03
forum: General Help
---

### Post by duf on 2008-03-03
Hi,

Is there a way to re-install Ubuntu 7.10 with the same programs that I have now on my computer. I messed some things up using 'rm' and removing those programs with 'apt-get purge' doesn't help. So i thought it would perhaps be easier and faster to re-install Ubuntu.

Perhaps saving the packaging lists or something. It takes a lot of time to choose the packages, I want.

Could I save the package list and use that with a new install.?

Thanks for any help

---

### Post by zvacet on 2008-03-03
**dpkg --get-selections > installed-software**

After this command you will find file in home directory with list of all installed packages.You can e-mail it to yourself and after you make reinstall put that file in home directory and 

**dpkg --set-selections < installed-software**

**dselect**

that will download and install all packages for you.Other potion is to use APTonCD(it is in synaptic).With it you will make iso of var/cache/apt/archives and that is a place where are all packages saved if you install them with apt-get or synaptic.But if you ever run **apt-get clean **or **apt-get autoclean** this option is not valid,because with these commands you deleted what you are trying to save now.If that is the case use first option.

---

### Post by duf on 2008-03-03
That's what i need !
Thank you ZVACET

---

