---
title: "Inconsistent hdparm causing crash and cannot be removed/replaced!!"
date: 2006-12-12
forum: General Help
---

### Post by a_l_a_n on 2006-12-12
[Apologies for posting all over the web]

I have a problem with hdparm (or at least thats how it manifests itself).

I was trying to upgrade from Kubuntu Dapper to Kubuntu Edgy. It crashed during the package installation. I tried to resume it but it always crashes when it gets to hdpram.

Initially it complained about /etc/init.d/hdpram and /etc/udev/rules.d/85-hdparm.rules. Sure enough the foremer was empty and the latter totally corrupt. I replaced them with ones from a deb file I downloaded. Now it just crashes without any special notice. Every time, my computer just switches off.

I tried to purge it with dpkg but it complains about it being inconsistent and suggests I reinstall and then remove it, but of course the whole point is I cannot install it.

I tried to go back to dapper sources and run apt-get upgrade but same result. I cannot complete my upgrade until hdparm is sorted out and I cannot find anyway to reinstall or remove it. HELP!

Note: I have been experiencing a problem for a week now which may be related. I have found that running updatedb causes the same instant shut off. Also I think it has crashed in response to a find command. I have been unable to figure out the cause of this. My best guess is that my hard disks are somewhat corrupt ... indeed I get many messages to that effect during boot, but whether this is the cause or just a symptom and what to do about it I dont know.

HELP!!

---

