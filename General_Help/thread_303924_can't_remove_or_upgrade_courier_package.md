---
title: "can't remove or upgrade courier package"
date: 2006-11-21
forum: General Help
---

### Post by jmmert on 2006-11-21
after upgrading to xubuntu to edgy i get an error with synaptic that the courier package has broken dependencies, specificaly the courier-authdaemon which I can't remove or upgrade. Synaptic shows courier-authdaemon.47-13ubuntu5.1 installed but it needs to be upgraded to .58-4ubuntu1. I have run the dpkg --configure -a but that does not fix the problem. Any solutions?  I'm not worried about saving any config files for courier.

---

### Post by ingo on 2006-11-22
what does 

sudo apt-get install -f 

do? you perhaps lacking repositories?

---

### Post by jmmert on 2006-11-24
thanks for the reply, yes I did not have the repos. but I downloaded it and reinstalled the older version then immediately removed the package.  It seems you can't upgrade that package without removing it first.

---

