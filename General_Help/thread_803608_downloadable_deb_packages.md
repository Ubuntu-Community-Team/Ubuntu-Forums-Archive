---
title: "downloadable deb packages"
date: 2008-05-22
forum: General Help
---

### Post by mephisto56 on 2008-05-22
If I download a third party deb and install it, will it interfere with normal ubuntu packages in any way? Will it be upgraded if I download an updated deb and istall that?

---

### Post by Cap'n Skyler on 2008-05-22
not all deb packages will ,but MOST are fine.of the ones i have used,never had any issues with the debs.
if you look in synapatic at each package choice,you will see even now some of the 'Buntu applications are sourced from debian.
you should be ok,but do post back if you have any issues.
and welcome to teh forums:popcorn:

---

### Post by mephisto56 on 2008-05-22
Most are fine? So they can render the package management unstable?

---

### Post by Irony on 2008-05-22
3rd party packages aren't supported in Ubuntu, having said that I've used a number of third party packages over the years and haven't had any problems.

Just keep a back-up of your system and when installing copy the output of the terminal list so that you can uninstall everything if you need to.

---

### Post by madjr on 2008-05-22
[http://getdeb.net/](http://getdeb.net/)

---

### Post by mephisto56 on 2008-05-22
> **Irony said:**
> 3rd party packages aren't supported in Ubuntu, having said that I've used a number of third party packages over the years and haven't had any problems.

Just keep a back-up of your system and when installing copy the output of the terminal list so that you can uninstall everything if you need to.

If I interpret this correct, you install a a package, the dependencies are handled by Ubuntu, and after uninstall the dependencies are kept in the system? Second, that also means the dependencies are updated by Ubuntu?

---

### Post by shifty_powers on 2008-05-22
fi you want to get rid of unused dependencies and files do:

```
sudo apt-get autoclean
```

---

### Post by Cap'n Skyler on 2008-05-22
> **mephisto56 said:**
> Most are fine? So they can render the package management unstable?

what i mean is,there has to be a few odd packages that may cause problems.they have like 18,000? packages available.i read in the last week
from the canonical site an interview with Mark Shuttleworth and it was said in the interview that 'buntu and debian come from the same ,but by now there is a small degree of separation.i assume most of this is in how the non free drivers are handled.so i think you will be fine to use debs just keep in mind it MIGHT have an odd issue with one of 18,000 pieces of software.i never worried much when i used debs.nor did i worry when i got some linux software to work on my son's MAC.
linux software being open,is fairly certain to be workable across linux distros.
  i doubt you have any significant fears that are real.go for it-- but do back up or image you system in case.
Moofs:guitar:

---

### Post by Irony on 2008-05-22
> **mephisto56 said:**
> If I interpret this correct, you install a a package, the dependencies are handled by Ubuntu, and after uninstall the dependencies are kept in the system? Second, that also means the dependencies are updated by Ubuntu?

Yes - however if you install deborphan (which finds orphaned dependencies), you can uninstall these dependencies (or if you kept a record of the install you could uninstall them as well); I use deborphan and it works very well.

---

### Post by mephisto56 on 2008-05-24
According to the post above deborphan isn't necessary. sudo apt-get autoclean would be enough if I'm correct.

---

### Post by Irony on 2008-05-29
No, autoclean just clears out cached packages that are no longer available in the repositories - being a tidy freak I personally have synaptic clear out these caches as soon as a program is installed.

---

