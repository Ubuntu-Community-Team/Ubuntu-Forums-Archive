---
title: "ubuntu 12.04.02 kernel?"
date: 2012-10-27
forum: General Help
---

### Post by ELD on 2012-10-27
I read that the plan was to have kernel 3.5+ in Ubuntu 12.04.2 is that still the plan?

---

### Post by Linuxisfast on 2012-10-27
The LTS kernel throughout its lifetime gets regular kernel patches from upstream kernel on a need to use basis after thorough testing so that makes kernel update unnecessary. In case you want a new kernel, you can get unpatched and not tested new kernel from mainline kernel ppa.

---

### Post by ELD on 2012-10-27
> **Linuxisfast said:**
> The LTS kernel throughout its lifetime gets regular kernel patches from upstream kernel on a need to use basis after thorough testing so that makes kernel update unnecessary. In case you want a new kernel, you can get unpatched and not tested new kernel from mainline kernel ppa.

I know that, i am talking about the 12.04.2 point release where there was plans for a newer kernel.

I am looking to see if anyone knows if it is still happening.

---

### Post by Linuxisfast on 2012-10-27
> **ELD said:**
> I know that, i am talking about the 12.04.2 point release where there was plans for a newer kernel.

I am looking to see if anyone knows if it is still happening.

LTS never gets kernel upgrades as that has been their policy for LTS, where did you read they are going for new kernel?

---

### Post by ELD on 2012-10-27
It was one of the discussed features for Ubuntu 12.04 to get newer kernels, i can't remember the exact link.

---

### Post by father_ted on 2012-10-27
i believe 12.04.2 will get a 3.5 series kernel.

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

---

### Post by AlexDudko on 2012-10-27
> **father_ted said:**
> i believe 12.04.2 will get a 3.5 series kernel.

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

This is not an officially supported kernel for Ubuntu-12.04 LTS.
Are there any reasons to use 3.5 kernel in the LTS version instead of the officially supported one? Are you going to upgrade some hardware which is supported only from 3.5 kernel?

---

### Post by father_ted on 2012-10-27
The hardware enablement initiative seems to be going to make this official.

[http://www.omgubuntu.co.uk/2012/08/omg-interviews-leann-ogasawara-canonical-kernel-team-manager-marathoner-and-mother](http://www.omgubuntu.co.uk/2012/08/omg-interviews-leann-ogasawara-canonical-kernel-team-manager-marathoner-and-mother)
[http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel](http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel)

---

### Post by Linuxisfast on 2012-10-27
*For those unaware, we intend to provide the 12.10 kernel and X stack for enablement purposes in 12.04*


The word is **enablement**

---

### Post by AlexDudko on 2012-10-27
> **father_ted said:**
> The hardware enablement initiative seems to be going to make this official.

[http://www.omgubuntu.co.uk/2012/08/omg-interviews-leann-ogasawara-canonical-kernel-team-manager-marathoner-and-mother](http://www.omgubuntu.co.uk/2012/08/omg-interviews-leann-ogasawara-canonical-kernel-team-manager-marathoner-and-mother)
[http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel](http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel)

"The 3.2 kernel released with 12.04 will continue to be maintained for the life time (5 years) of precise."
What's the difference then between this policy and Ubuntu-10.04 backporting newer kernel versions?

---

### Post by cmcanulty on 2012-10-27
are you sure it wasn't gnome 3.5 they were saying

---

### Post by Chogan on 2012-12-26
12.04.2 will include Kernel 3.5, or maybe 3.6, along with a newer Xorg, as part of the **hardware enablement package**, which is already available for pre-release testing.
  [https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport]("https://launchpad.net/%7Eubuntu-x-swat/+archive/q-lts-backport")
  The 3.2 kernel released with 12.04 will continue to be maintained for  the life time (5 years) of precise. (and also Debian Wheezy)
  
[LIST]
[*]Also, Ubuntu will generally work with mainline kernels. Binary builds are provided by the kernel team. [https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[/LIST]
  **This is a new policy. The decision to have such a updated kernel and  Xorg was decided at the 2012 Ubuntu Developer Summit (UDS) in Oakland.**
  The most exciting feature about 3.5 (IMHO), Seccomp2, is part of the Precise 3.2 kernel.
  
[LIST]
[*][http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads)
[*][http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/testcases/1301/results](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/testcases/1301/results)
[/LIST]
[RIGHT][**Source**]("http://askubuntu.com/questions/168218/will-ubuntu-12-04-1-include-the-new-linux-kernel")[/RIGHT]

---

