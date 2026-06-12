---
title: "How to install ndiswrapper on an offline system?"
date: 2007-01-10
forum: General Help
---

### Post by phossal on 2007-01-10
An Ubuntu user may need to install ndiswrapper on their offline system. I know it's possible to build rpms on another machine, and then move them to the package.

What's the easiest way? Can I get a step-by-step how-to?

---

### Post by aysiu on 2007-01-10
*ndiswrapper-utils* is on the installer CD.

Type these commands in the terminal: ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```

---

### Post by phossal on 2007-01-10
I suspected it was on the CD, which is a good source for the guy who needs it, thank you.
ndiswrapper is needed [here]("http://ubuntuforums.org/showthread.php?p=1996445#post1996445")

---

