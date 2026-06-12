---
title: "package is in a very bad inconsistent state"
date: 2020-01-19
forum: General Help
---

### Post by adidacta on 2020-01-19
Hi
I installed Pulse, a VPN client. it did not install well and now I can't reinstall or remove it and any other install now fails.
[B]This:
[/B]*sudo dpkg -r pulse*

[B]Give me this:
[/B]*package is in a very bad inconsistent state; you should*
* reinstall it before attempting a removal*
*Errors were encountered while processing:*
* pulse*

[B]This:
[/B][I]sudo apt --fix-broken install
[/I]**Gives me this:**
*Reading package lists... Done*
*Building dependency tree       *
*Reading state information... Done*
[I]E: The package pulse needs to be reinstalled, but I can't find an archive for it

[/I][B]And this (installing another package):
[/B][I]sudo apt install gnome-tweak-tool -y
[/I]**Gives me this:**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package pulse needs to be reinstalled, but I can't find an archive for it.


I also get this error


[ATTACH=CONFIG]284825[/ATTACH]



What can I do?

---

### Post by Impavidus on 2020-01-19
Pulse has to be reinstalled before it can be cleanly removed. Removal of packages can be forced, but that will leave junk around, wich may cause issues later, so I never do that. pulse is not in the official repositories, so where did you get it? Enable the source, download the deb or find it in your downloads directory or wherever you've stored it, then install it, then remove.

Which release of Ubuntu do you use?

---

