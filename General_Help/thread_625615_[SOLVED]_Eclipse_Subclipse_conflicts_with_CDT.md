---
title: "[SOLVED] Eclipse: Subclipse conflicts with CDT"
date: 2007-11-28
forum: General Help
---

### Post by rockballad on 2007-11-28
Hi,

I installed Eclipse CDT successfully, and ran some examples ok. But after I install Subclipse ([http://subclipse.tigris.org/update_1.2.x](http://subclipse.tigris.org/update_1.2.x)) then C/C++ perspective disappeared, and I couldn't build a C/C++ project any more. Could you tell me if you have the same problem?

Thanks!

---

### Post by aitorcalero on 2007-11-28
I does not have sense to me, since Subclipse and C/C++ are not related. Whay don't you try to create a new workspace. It could be also that you need to search C/C++ in the tiny perspective button (up right) under the "other..." option.

---

### Post by rockballad on 2007-11-28
> **aitorcalero said:**
> I does not have sense to me, since Subclipse and C/C++ are not related. Whay don't you try to create a new workspace. It could be also that you need to search C/C++ in the tiny perspective button (up right) under the "other..." option.

Thank you, I think so, they're not related to each other, but it's the fact. I tried many times, but always like that. Install Eclipse (offline from zip file), install CDT plugin (offline, too) - build C++ project ok. Install Subclipse (online, from repo) - and C/C++ perspective lost. I open up the Perspective dialog (click on "Other...") but C/C++ is not on the list.

:confused:

I'm going to install Subclipse offline, could it help :confused:

---

### Post by rockballad on 2007-11-28
Yeah! When I was trying to discuss with you, I wondered that if I could install subclipse in offline. And it works for me! I setup all eclipse, CDT, subclipse in offline mode (use compressed files). After that, run eclipse with -clean option. They work together now!

Thank you all!

---

