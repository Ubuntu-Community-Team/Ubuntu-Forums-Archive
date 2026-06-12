---
title: "How get my program in a ubuntu repository?"
date: 2018-10-08
forum: General Help
---

### Post by gosim2 on 2018-10-08
Hello, I have created a program and would like it to be in the Ubuntu repository. I looked at snapcraft but it was impossible to understand. The program is a Simulink variant that uses Octave as a mathematical engine. I think it is a nice program. So how do I get it in the repository? Thanks in advance.

---

### Post by Tadaen_Sylvermane on 2018-10-08
Id suggest a ppa to start. See what happens after that.

---

### Post by deadflowr on 2018-10-09
See: [http://packaging.ubuntu.com/html/packaging-new-software.html#submitting-for-inclusion]("http://packaging.ubuntu.com/html/packaging-new-software.html#submitting-for-inclusion")

---

### Post by gosim2 on 2018-10-09
thank you for your help :)

---

### Post by deadflowr on 2018-10-09
There is also the alternative snap method:
[https://developer.ubuntu.com/snapcraft]("https://developer.ubuntu.com/snapcraft")
Snaps, as opposed to the normal apt-based packages, can get uploaded to current distributions quickly.
Where as a new normal apt-based packages would not be able to be uploaded until at least the next development cycles.
(And that's if your lucky and the package passes muster)

(Current releases are frozen with the packages set in stone; with a few exceptions.
PPAs are a work around for that, as PPAs aren't as restricted. 
More here: [https://help.launchpad.net/Packaging/PPA]("https://help.launchpad.net/Packaging/PPA"))

---

### Post by gosim2 on 2018-10-10
> **deadflowr said:**
> There is also the alternative snap method:
[https://developer.ubuntu.com/snapcraft](https://developer.ubuntu.com/snapcraft)
Snaps, as opposed to the normal apt-based packages, can get uploaded to current distributions quickly.
Where as a new normal apt-based packages would not be able to be uploaded until at least the next development cycles.
(And that's if your lucky and the package passes muster)

(Current releases are frozen with the packages set in stone; with a few exceptions.
PPAs are a work around for that, as PPAs aren't as restricted. 
More here: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA))


I will try snapcraft again, I think it is the best concept but it was impossible for me to understand how to use it. 
Thanks again. :popcorn:

---

