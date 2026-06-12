---
title: "List of updates being held back ?"
date: 2024-08-23
forum: General Help
---

### Post by sussexlad on 2024-08-23
Hi.
I'm currently running 22.04.4LTS and 'sudo apt upgrade'  returns  6 not to upgrade.
Is there anywhere I can confirm this situation is up to date ? i.e I haven't missed anything?
It's just that the three update packages have been there for ages!

Thanks.

---

### Post by &amp;KyT$0P# on 2024-08-23
Please post the output from running this command in Terminal -
```
apt list --upgradable
```

You can check [here]("https://ubuntu-archive-team.ubuntu.com/phased-updates.html") to see if the not-to-upgrade packages maybe [phased updates]("https://wiki.ubuntu.com/PhasedUpdates") that your system just hasn't been phased into yet.

---

### Post by sussexlad on 2024-08-23
Thanks for the reply. Output as below.

andy@andy-OptiPlex-9020:~/Desktop$ apt list --upgradable
Listing... Done
libpython3-stdlib/jammy-updates 3.10.6-1~22.04.1 amd64 [upgradable from: 3.10.6-1~22.04]
python3-minimal/jammy-updates 3.10.6-1~22.04.1 amd64 [upgradable from: 3.10.6-1~22.04]
python3-update-manager/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.19]
python3/jammy-updates 3.10.6-1~22.04.1 amd64 [upgradable from: 3.10.6-1~22.04]
update-manager-core/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.19]
update-manager/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.19]

---

### Post by &amp;KyT$0P# on 2024-08-23
All of those are phased updates where phasing has been stopped (0% of systems are phased into the update).  You can safely ignore them.

---

### Post by sussexlad on 2024-08-23
Thanks for the prompt response. Cheers.

---

### Post by michael351 on 2024-08-31
> **halogen2 said:**
> All of those are phased updates where phasing has been stopped (0% of systems are phased into the update).  You can safely ignore them.

Just curious what will happen to these packages? I see these three at 'phased 0%' for many months now. This seems unusually long time.
The following packages have been kept back on my system:
  python3-update-manager update-manager update-manager-core (shim-signed is also held back, but is phasing (currently at 29%)).

---

