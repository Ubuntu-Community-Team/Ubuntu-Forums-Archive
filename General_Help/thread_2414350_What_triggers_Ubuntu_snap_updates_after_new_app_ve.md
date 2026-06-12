---
title: "What triggers Ubuntu snap updates after new app version is published?"
date: 2019-03-09
forum: General Help
---

### Post by maglin2 on 2019-03-09
I run chromium snap.

The current stable version was published on 3rd March, as shown here [https://snapcraft.io/chromium](https://snapcraft.io/chromium)

On 7th March I read that this latest chromium version patched a FileReader vulnerability (CVE-2019-5786) for which there was a known zero day exploit.

I checked my running version, and it had not been updated. I forced an update through snap refresh, which gave me the latest (patched) stable version published on 3rd March.

According to this [https://docs.snapcraft.io/keeping-snaps-up-to-date/7022](https://docs.snapcraft.io/keeping-snaps-up-to-date/7022) snap checks for updates 4 times daily, yet I received no update in the 4 days after publication. I'm trying to figure out why.

Do Ubuntu have their own separate trigger for releasing snap updates perhaps? That would seem odd, given that canonical publish the chromium snap.

Is the update check at odd times like 2-5am, when my machine would be not be running?

Anyone know?

Thanks

---

