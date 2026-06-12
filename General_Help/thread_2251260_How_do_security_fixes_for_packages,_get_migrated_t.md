---
title: "How do security fixes for packages, get migrated to LTS repositories?"
date: 2014-11-03
forum: General Help
---

### Post by mikodo on 2014-11-03
Very, "basically".

Say, a package, has released security fixes in Debian "Unstable" repositories. Then the Debian Security Team, would migrate them to the current "Stable". How do these fixes get migrated to Ubuntu LTS repositories? Is there a similar Ubuntu Security Team, that attends to the LTS repositories, in a similar fashion?

---

### Post by buzzingrobot on 2014-11-03
Yes: [https://wiki.ubuntu.com/SecurityTeam](https://wiki.ubuntu.com/SecurityTeam).

---

### Post by ian-weisser on 2014-11-03
Example:  Let's say that a vulnerability is discovered in libfoo1.3, and the world learns about it through a CVE.

- The upstream releases a patch, and perhaps also releases a new version libfoo1.4 that includes the patch plus other new features.

- The Ubuntu Security Team picks up the CVE, patches the released versions of Ubuntu (10.04 server, 12.04, 14.04, 14.10), and uploads them to the -security repo as libfoo1.3~ubuntu2. Debian is not involved with this process. Released versions of Ubuntu get the patch, but not libfoo1.4 - that would be a backport).

- When libfoo1.4 moves to Debian Unstable, it gets (mostly automatically) imported into Ubuntu 15.04.

That's an overview of the flow. It's a bit more complex, and there are a few more contingencies than that.

---

### Post by mikodo on 2014-11-03
Thank you, folks.

... following links, about "CVE" and Security Teams.

---

