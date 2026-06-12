---
title: "Accessing Package Changelogs: How to"
date: 2021-09-01
forum: General Help
---

### Post by scorp123 on 2021-09-01
I got asked this once... and I kind of feel bad because I remember that I gave an incomplete + borderline incorrect answer ](*,)

But I can't find that thread anymore. So I'll create a new one:

**How can one *easily* access the changelog of a package to see what has been changed / patched / updated?**


_Answer:_

There's a command for that. And if you have "Cockpit" installed you can also check in the "Software Updates" section. I am not sure what other GUI methods exist, sorry about that.

```
apt changelog packagename
```

So let's assume you notice that there's an update for the package **ntfs-3g** and you're wondering *"Geee, what happened... What did they change?"* so you can type this into a terminal:

```
apt changelog ntfs-3g
```

... and you'd see this output:

```
ntfs-3g (1:2017.3.23AR.3-3ubuntu1.1) focal-security; urgency=medium

  * SECURITY UPDATE: multiple security issues
    - debian/patches/aug2021-security.patch: backport fixes from new
      upstream version.
    - No CVE number

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Mon, 23 Aug 2021 09:18:46 -0400

ntfs-3g (1:2017.3.23AR.3-3ubuntu1) eoan; urgency=low

  * Merge from Debian unstable.  Remaining changes:
    - Don't install /bin/ntfs-3g as setuid root.
  * Dropped changes, included in Debian:
    - debian/patches/0001-Fixed-reporting-an-error-when-failed-to-build-the-mo.patch:
      Fixed reporting an error when failed to build the mountpoint

 -- Steve Langasek <steve.langasek@ubuntu.com>  Thu, 02 May 2019 22:49:24 -0700

...
```

Please note that not every package will provide such details, e.g. the package **google-chrome-stable** does not:

```
> apt changelog google-chrome-stable

E: Failed to fetch changelog:/google-chrome-stable.changelog  Changelog unavailable for google-chrome-stable=93.0.4577.63-1
```

... but e.g. **firefox** does:

```
> apt changelog firefox

firefox (91.0.2+build1-0ubuntu0.20.04.1) focal; urgency=medium

  * New upstream release (91.0.2+build1)

 -- Olivier Tilloy <olivier.tilloy@canonical.com>  Mon, 23 Aug 2021 18:55:34 +0200

firefox (91.0.1+build1-0ubuntu0.20.04.1) focal; urgency=medium

  * New upstream release (91.0.1+build1)

 -- Olivier Tilloy <olivier.tilloy@canonical.com>  Mon, 16 Aug 2021 23:00:18 +0200

firefox (91.0+build2-0ubuntu0.20.04.1) focal; urgency=medium

  * New upstream release (91.0+build2)

 -- Olivier Tilloy <olivier.tilloy@canonical.com>  Thu, 05 Aug 2021 10:21:48 +0200

firefox (91.0+build1-0ubuntu0.20.04.1) focal; urgency=medium

  * New upstream release (91.0+build1)

  [ Rico Tzschichholz ]
  * Drop obsolete patches
    - debian/patches/relax-cargo-dep.patch
  * Update patches
    - debian/patches/armhf-reduce-linker-memory-use.patch
    - debian/patches/fix-armhf-webrtc-build.patch
    - debian/patches/rust-drop-dll-checksums.patch
    - debian/patches/ubuntu-ua-string-changes.patch
  * Bump build-dep on rustc >= 1.51.0 and cargo >= 0.52
    - debian/control{,.in}
  * Ignore Scots locale (sco)
    - debian/config/locales.blacklist

...
```

I hope this post may prove useful to someone one day.

---

