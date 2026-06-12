---
title: "Dependency libc6 cannot be satisfied"
date: 2007-09-16
forum: General Help
---

### Post by ketzerei on 2007-09-16
I've read several other posts and cant seem to find an answer. I'm trying to install Muine and every time I install it, it wont run. When I use gdebi and install a .deb instead, its says 'dependency is not satisfiable: libc6' and doesnt work. What irritates me is that 'sudo  apt-get install muine' works, but it wont run. Help appreciated.

---

### Post by cubeist on 2007-09-16
fire up synaptic package manager (System/Administration/) and search for libc6.  If it is not installed... install it... if it already is installed try re-installing it or remove it and re-add it...

---

### Post by ketzerei on 2007-09-16
wont that break my system?

---

### Post by atlfalcons866 on 2007-09-16
i had this issue when i was trying to install a kernel i compiled onto another Ubuntu box. I couldn't find a fix so i had to recompile the kernel and wait for another 4 hours because of the libc6.:(

---

### Post by cubeist on 2007-09-16
> **ketzerei said:**
> wont that break my system?

I have it installed and my system isn't broken... although I don't remember specifically downloading it... so it either came with part of the base ubuntu install or it was added automatically as a dependency.

I have never had my system "break" just by installing something from synaptic... but it is up to each user to read the release notes to understand exactly what they are installing, what it is used for, and where it may cause incompatibilities...

---

