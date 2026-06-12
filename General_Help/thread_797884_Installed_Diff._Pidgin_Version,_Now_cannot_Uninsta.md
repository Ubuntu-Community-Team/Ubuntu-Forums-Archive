---
title: "Installed Diff. Pidgin Version, Now cannot Uninstall it"
date: 2008-05-17
forum: General Help
---

### Post by PRGUY85 on 2008-05-17
Hey:

I had Pidgin installed through Synaptic but decided to switch to Funpidgin.  I uninstalled everything Pidgin related on Synaptic and forced a i386 deb package of FunPidgin to install in my 64-bit setup.  After that I didn't know how to exactly uninstall Funpidgin, but I used: "dpkg --purge funpidgin"  and thought it did the trick.

Afterwards, I installed packages from the following site:

[http://echelon89.altervista.org/annunci/notizie-flash/pidgin-2.4.2devel-29.04.2008-debs-per-ubuntu-hardy.html](http://echelon89.altervista.org/annunci/notizie-flash/pidgin-2.4.2devel-29.04.2008-debs-per-ubuntu-hardy.html)

Now, I want to start fresh with Pidgin but since I've got no Pidgin installed through Synaptic, I don't know how to get rid of everything I installed.


Any help?

---

### Post by PRGUY85 on 2008-05-19
Bump?

---

### Post by PRGUY85 on 2008-05-19
I tried:

sudo dpkg -r pidgin
sudo dpkg -r funpidgin

It says none of them are installed.

I tried:

sudo dpkg --purge pidgin
sudo dpkg --purge funpidgin

Gave me same answer.

Yet, the Pidgin icon is still on my Internet menu and if I click it the program comes up.

---

