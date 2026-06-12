---
title: "Lubuntu archive download issues"
date: 2014-09-12
forum: General Help
---

### Post by hsh97365 on 2014-09-12
Maybe this has been solved before but searches give me different solutions and they don't seem to work.

For context:
I have installed a variant of Lubuntu (it's an older variant, I don't know which version). This laptop has had wireless adaptor issues (broadcom), which I then solved with rfkill unblock all.

However, it seems there are other issues. No installs, packages or archives will download. At first, I thought it was because the GB servers were down, so I switched to US, then general, but the downloads kept timing out. I switched back to the GB.archive servers afterwards.

I have no idea what is causing the issue, but it's preventing me from installing software packages I'm quite in need of. How do I diagnose and fix the issue?

Thanks for any assistance!

---

### Post by Dennis N on 2014-09-12
It's possible the version of Lubuntu your variant is based on is no longer supported. The repositories it needs may be closed - only the 14.04 release is currently supported.

---

### Post by hsh97365 on 2014-09-12
Version 13.04

But if that's the case, how does one update if the update doesn't download?

---

### Post by uRock on 2014-09-12
I believe 12.04 and 14.04 are the only Lubuntus currently supported.

---

### Post by Dennis N on 2014-09-12
> **hsh97365 said:**
> Version 13.04

But if that's the case, how does one update if the update doesn't download?

There is a time window for upgrading to the next version without doing a new install. Using Lubuntu as an example:

If you want to upgrade 13.04 (not a new install) you could get to the next version 13.10 (you can't skip a version to 14.04) as long as the 13.10 repositories are still open to obtain the newer software packages. 

But if you wait too long and the 13.10 repositories are closed, you can only do a new install of the 14.04.

---

### Post by Dennis N on 2014-09-12
> **uRock said:**
> I believe 12.04 and 14.04 are the only Lubuntus currently supported.

Lubuntu 12.04 was not an LTS, so there is no direct upgrade path to 14.04.

I suppose its underlying Ubuntu system packages are still being updated, but any Lubuntu specific packages are not receiving updates.

---

### Post by hsh97365 on 2014-09-14
According to this 12.04 is LTS:
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

However, the bridge to jump to 14.04 might be too far to leap to, judging by setup. I'm not in a position to reinstall and I'm not in a position to update (why isn't there some sort of manual download option or some such? Seems awfully inconvenient).

Is there some way I could 'downgrade' to 12.04? With LTS enabled I could then jump to 14.04.

---

### Post by Impavidus on 2014-09-14
Ubuntu, Kubuntu and Xubuntu 12.04 are LTS releases, Lubuntu 12.04 is not. 14.04 is the firts LTS release of Lubuntu ever, receiving 3 years of support. Because the other flavours are still supported the 12.04 repositories are still available, but upgrades to the still supported packages are not checked for compatibility with the Lubuntu specific packages, so things might break. There is no simple downgrade option like the upgrade option, only a new install. New versions of software can usually read config files of old versions, but not the reverse, making downgrading more complicated than upgrading.

To get to a supported release of Lubuntu, your only reliable option is a fresh install.

---

