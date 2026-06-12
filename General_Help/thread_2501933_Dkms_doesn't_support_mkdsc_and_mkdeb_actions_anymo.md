---
title: "Dkms doesn't support mkdsc and mkdeb actions anymore"
date: 2024-10-26
forum: General Help
---

### Post by jordan83 on 2024-10-26
Hi everyone,

I'm trying to install the facetimehd driver to enable the webcam in my Ubuntu installation on a MacBook Pro 11,4.
The driver works and now I'm at the point where I need to setup dkms to have the module re-compiled each time the kernel is upgraded.
[I'm following this guide.]("https://github.com/patjak/facetimehd/wiki/Installation#setting-up-dkms-auto-compile-on-kernal-update-1")

The problem is that at this point of the walkthrough I'm supposed to use 2 actions from dkms that are not supported anymore:

```
Build a Debian source package: # dkms mkdsc -m facetimehd -v 0.1 --source-only
Build a Debian binary package: # dkms mkdeb -m facetimehd -v 0.1 --source-only
```

Does anybody know which commands I could use in alternative to achieve the same result?
I'm not very familiar with dkms and/or with the process of creating deb packages, unfortunately.

Thank you!

---

