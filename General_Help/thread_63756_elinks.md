---
title: "elinks"
date: 2005-09-08
forum: General Help
---

### Post by arlie on 2005-09-08
I tried installing elinks but I got this message instead:

arlie@jackal:~$ sudo apt-get install elinks
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  elinks: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
          Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
E: Broken packages
~~~~~~~~~~~~~~~~~

I can see libc6 on synaptic as installed package as well as libidn11. So, what am I missing?

---

### Post by rafakl on 2005-09-09
download elinks directly from synaptic or do a:

sudo apt-get install elinks

---

### Post by arlie on 2005-09-09
[QUOTE=rafakl]download elinks directly from synaptic or do a:

sudo apt-get install elinks[/QUOTE]

Yes, I've done that already. See my edited post above.

---

