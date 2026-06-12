---
title: "ubuntu-base (in synaptic package manager"
date: 2004-11-16
forum: General Help
---

### Post by ae+ on 2004-11-16
Hi

I wanted to install 'sendmail' from the spm so apache and web apps can send mail, however it tells me to that to install sendmail i would need to also un-install 'ubuntu-base'.

before i do this - just thought i'd get some advice on what 'ubuntu-base' is, and whether i need it

thanks heaps

ae

---

### Post by HiddenWolf on 2004-11-16
Ubuntu-base is a meta package.
it does not contain any code itself, but it depends on what the ubuntu-developers think of as the core of the system.

You can uninstall it without any difficulty, however if you would do a dist-upgrade later, and would not install ubuntu-base or -desktop, it might be that some weird errors would occur.

For instance, a lot of people had a very slow system after upgrading to hoary, because of the fact they uninstalled ubuntu-desktop. The developers replaced the 'fam' package by 'gamin', and changed the dependency on ubuntu-desktop. However, these systems did not switch to gamin, causing slowdowns and some errors.

---

