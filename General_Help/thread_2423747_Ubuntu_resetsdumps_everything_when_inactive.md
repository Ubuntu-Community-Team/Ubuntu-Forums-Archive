---
title: "Ubuntu resets/dumps everything when inactive"
date: 2019-07-28
forum: General Help
---

### Post by David_OConnor on 2019-07-28
Ubuntu 19.04. Started when upgrading by 18.10. Clean install didn't fix. When inactive and returning to computer, everything will be closed improperly, every time. As if it's doing reboots or logging me out. In logs: `CRITICAL: We failed, but the whale is dead. Sorry`.

---

### Post by SeijiSensei on 2019-07-28
Like I just said to another poster, 19.04 is a development release. If you want a stable platform, use 18.04LTS.

---

### Post by David_OConnor on 2019-07-30
Not sure I buy that. Label everything non-LTS as a beta?

---

### Post by SeijiSensei on 2019-07-30
> LTS or &#8216;Long Term Support&#8217; releases are published every two years in April. LTS releases are the &#8216;enterprise grade&#8217; releases of Ubuntu and are utilised the most. An estimated 95% of all Ubuntu installations are LTS releases, with more than 60% of large-scale production clouds running on the most popular OS images - Ubuntu 18.04, 16.04 and 14.04 LTS.

Every six months between LTS versions, Canonical publishes an interim release of Ubuntu, with18.10 being the latest example. These are production-quality releases and are supported for their lifespan, with sufficient time provided for users to update, but these releases do not receive the long-term commitment of LTS releases.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

While Ubuntu might describe interim releases as "production-quality," from my experience here people have more problems with them than with the LTS releases. Also this is pretty telling:

> An estimated 95% of all Ubuntu installations are LTS releases

Non-LTS releases have only nine months of support. For ordinary users, there is simply no good reason to install a release with such a short lifespan unless there are specific applications or upgrades that you need for some purpose. "Getting the latest and greatest" is not alone a reason to run something that's not an LTS release. For most users any differences will be negligible.

I'm running 19.04 only because I wanted to see the latest version of KDE5 Plasma, and because I'm an experienced user who can usually fix problems on my own. Also Kubuntu has generally been a more stable platform over the past couple of years than vanilla Ubuntu with changes like the adoption and then dropping of [Unity]("https://arstechnica.com/information-technology/2018/05/ubuntu-18-04-the-return-of-a-familiar-interface-marks-the-best-ubuntu-in-years/") and [Wayland]("https://www.omgubuntu.co.uk/2018/01/xorg-will-default-display-server-ubuntu-18-04-lts"). I suspect what has been true for Kubuntu has also been true for flavors like Lubuntu and Xubuntu, but I have limited experience with them.

---

### Post by David_OConnor on 2019-07-31
Thanks for the info!

---

### Post by Autodave on 2019-07-31
I currently run Xubuntu 16.04 & 18.04 on various machines.  I learned a long time ago not to upgrade from one release to another: I once had 13 machines running just fine.  Upgraded all 13.  One worked without issues.  3 had minor issues which I resolved.  9 ended up getting clean installs after they all had way too many issues to fix.  Use the LTS releases and do clean installs after backing everything up.

---

### Post by TheFu on 2019-07-31
+1 for staying with LTS and avoiding n non-LTS, unless you are a developer or love finding bugs.

If you are a typical end-user, don't use non-LTS without a very good reason, like your hardware is 1 week old from the vendor and the last LTS doesn't have the support backported, yet.  In 6-12 months, that support will be backported, so think on the non-LTS install for play reasons.  If your hardware is 12 months old, use the HWE install of the LTS and be happy.

---

