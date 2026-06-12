---
title: "Upgrading Packages with Beta Repositories"
date: 2007-09-04
forum: General Help
---

### Post by steve_c on 2007-09-04
I'll try to keep this clear and concise.

I'm administrator for roughly a dozen workstations and half a dozen servers. Most of the workstations run Ubuntu 7.04.

We have one user who needs the latest version of a program (Vim 7.1), for which there is no package in the Feisty repository. Since there is a package for it in the Gutsy repository I tried adding that and upgrading VIM, but then it wanted to upgrade a whole host of other things (libc6, libncurses5, etc) that are used by a whole lot more than just VIM. That makes me nervous about breaking things with the updates.

I realize just compiling from source would probably solve my problems, or even just a binary tarball. If I can use apt/synaptic it would be highly preferable since I have to administer more than just this machine. I know VIM probably isn't the type of thing that needs upgraded several times a year but for future reference it would be nice to know how to do it some way that allows the system to manage updates.

Thank you!

---

