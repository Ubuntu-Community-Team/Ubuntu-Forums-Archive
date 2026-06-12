---
title: "libxine-main1: Conflicts: libxine1 but 1.1.2+repacked1-0ubuntu3.2 is to be installed"
date: 2007-02-13
forum: General Help
---

### Post by picpak on 2007-02-13
Hey guys,

I'm trying to upgrade from Dapper to Edgy, but every time I do, it holds back hpijs and ubuntu-minimal. When I try to install these, I get this error:

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libxine-main1: Conflicts: libxine1 but 1.1.2+repacked1-0ubuntu3.2 is to be installed
E: Broken packages
```

I'd remove libxine-main1, but that removes xfmedia, which removes xubuntu-desktop, which then removes...ahh, it's one big mess. How can I fix this?

---

### Post by picpak on 2007-02-13
Well, I solved it...

I had to download libxine1 from [http://archive.aardvarque.com/ubuntu/misc/pool-dapper/](http://archive.aardvarque.com/ubuntu/misc/pool-dapper/) .

(Any reason why this isn't in the Dapper repos?)

---

