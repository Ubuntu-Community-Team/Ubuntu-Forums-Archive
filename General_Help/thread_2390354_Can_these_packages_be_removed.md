---
title: "Can these packages be removed?"
date: 2018-04-28
forum: General Help
---

### Post by speartip on 2018-04-28
I have been updating my Ubuntu-Budgie install since beta1.
I have noticed in synaptic that I have 4 packages in "Installed (Local or Obsolete)" which are libdns-export169, libdns169, libisc-export-166 & libisc166.
If I run "ubuntu-support-status --show-all" in a terminal, it is showing these 4 packages as "no longer downloadable".
So my Questions are, what are these packages for? & are they safe to remove?

---

### Post by PaulW2U on 2018-04-28
> **speartip said:**
> I have been updating my Ubuntu-Budgie install since beta1.
I have noticed in synaptic that I have 4 packages in "Installed (Local or Obsolete)" which are libdns-export169, libdns169, libisc-export-166 & libisc166.
If I run "ubuntu-support-status --show-all" in a terminal, it is showing these 4 packages as "no longer downloadable".
So my Questions are, what are these packages for? & are they safe to remove?
As the development of a release progresses many packages are updated. Sometimes the package retains the same name but the version number changes and sometimes the package is renamed. If the version number changes then the new package replaces the old one but if a package is renamed then both new and old can exist which is what has happened here.

I too installed 18.04 early and saw these packages become redundant in synaptic

libdns169 was replaced by libdns1100. libdns-export169 was replaced by libdns-export1100. libsic-export166 was replaced by libisc-export169. libisc166 was replaced by libisc169.

You've already found that these packages are not downloadable which means that they're not part of the 18.04 release. If you had installed 18.04 from the release ISO you would only have seen the renamed packages. So yes, go ahead and use synaptic to remove them from your system making sure that nothing else is removed along with them.

---

### Post by speartip on 2018-04-28
Thanks PaulW2U...
Your explanation makes sense. I have now removed all the (Local or Obsolete) packages, & will mark this thread as solved.

---

