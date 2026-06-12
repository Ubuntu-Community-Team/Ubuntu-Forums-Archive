---
title: "will OpenZFS ever be updated?"
date: 2024-01-27
forum: General Help
---

### Post by dchmelik on 2024-01-27
Will OpenZFS ever be updated?  Ubuntu apparently has v2.1.5 (almost two years old) but OpenZFS (formerly ZFSOnLinux) is seven versions ahead: v2.2.2 (updated last month).  A saying is "Debian's repository is China old" but even Debian/Devuan is ahead of Ubuntu, on v2.1.11!  Lately I can't update Ubuntu-based OS in chroots because ZFS is too old.

---

### Post by MAFoElffen on 2024-01-27
What are you talking about?

Jammy 22.04.3 is 2.1.5-1ubuntu6~22.04.2... But includes backports from 2.2.2

RE: [https://bugs.launchpad.net/ubuntu/mantic/+source/zfs-linux/+bug/2044657](https://bugs.launchpad.net/ubuntu/mantic/+source/zfs-linux/+bug/2044657)

You can see from my comments there, I was testing Noble with, and it is currently due to release with 2.2.2.

I update ZFS chroots from Jammy, Mantic and Noble. Where are you having a problem?

---

### Post by avidandrew on 2024-02-01
Each Ubuntu release freezes packages at a specific version right before the release. For stability reasons, no more updates are made to that release (e.g. 20.04, 22.04, 24.04, etc) unless there's a really good reason (like a significant bug or security vulnerability). See here for details:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Ubuntu 24.04, aka noble, coming out in April will have OpenZFS 2.2.2:
[https://packages.ubuntu.com/noble/zfsutils-linux](https://packages.ubuntu.com/noble/zfsutils-linux)

If this "freeze-for-each-release" method isn't to your liking, you could look at a rolling release distro like Arch Linux where the packages are updated immediately.

---

### Post by dchmelik on 2024-02-23
Of course, I was talking about Ubuntu 22.04.3.  I didn't see the backport available.

---

### Post by ian-weisser on 2024-02-24
If you are using a two-year-old release of Ubuntu, then seeing two-year-old packages in it seems reasonable.

For newer packages, look at newer releases of Ubuntu.

Freeze-at-release (except patches) ensures that the wide variety of dependencies remain stable across the life of the release. It's been a key characteristic of Debian-based distros for over 20 years.

---

### Post by dchmelik on 2024-02-24
MAFoElffen said Ubuntu v22.04.3 has a ZFS backport.  Avidandrew said if there's significant bugs--which there are in this case (filesystem data loss)--then updates are made.  Are these are really true?

---

### Post by ian-weisser on 2024-02-24
True. Several bugfixes have indeed been backported to older versions of zfs. You can tell by the package version string.

Patching is the typical behavior for Debian-type distros like Ubuntu. Bumping a version after release is very rare (all the resulting breakage risks causing more problems than it solves), and usually links to a specific CVE.

---

### Post by MAFoElffen on 2024-02-26
Now at 22.04.4... 2\DEV 24.04 has had zfs-linux for months now. 1 fallen and I made sure of that and where the dev testers for that...

The reason it is getting backported down through 20.04, is that it is linked to a CVE: [https://nvd.nist.gov/vuln/detail/CVE-2023-49298](https://nvd.nist.gov/vuln/detail/CVE-2023-49298)

When you talk about Security Updates, those going applied to the next LTS release (April, 24.04), applied to latest current, and backported to all supported releases.

As for this statement:
> **avidandrew said:**
> Each Ubuntu release freezes packages at a  specific version right before the release. For stability reasons, no  more updates are made to that release (e.g. 20.04, 22.04, 24.04, etc)  unless there's a really good reason (like a significant bug or security  vulnerability). See here for details:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
Sort of true, if you clarify the statement (first sentence) further: About 1-2 weeks before a DEV version gets officially released as the public release version (from beta to live), that specific repo gets frozen. This is before a release is released. When we are dev testoing, a lot of it in the dailys are pieces of things they want us to test, or see if something works. It isn't necessarily the finished product. Magic is happening behind the scenes during that time to put together all the pieces. I am still surprised by some things when the final ISO is released, in how they put those together. 

But this "issue" is already resolved in 24.04. Mentioning 20.04, 22.04 in that same statement, is where that falls off, as not related to the same thing. Their repo's do not get frozen. They are already released... This has nothing to do with the backports to the existing LTS versions that are still in support.

---

