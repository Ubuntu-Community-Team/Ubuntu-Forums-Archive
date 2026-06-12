---
title: "&quot;unstable&quot; name in kernel PPA"
date: 2015-06-25
forum: General Help
---

### Post by Aide9aic on 2015-06-25
I regularly install the newer kernels from the [Ubuntu kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). As described [in the wiki]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), the directories have typically been named in the format ***<tag>*-*<series>***. But starting with 4.1-RC3, the format has changed to ***<tag>*-unstable**. I've been running 4.1 since it appeared, and I'm not experiencing any instability.

The **BUILT** file for v4.1-rc2-vivid contains:
```
Release: precise
Host: gomeisa
Start: 1430710516
Debian: vivid
Configs: Ubuntu-3.19.0-16.16
End: 1430714261
```

Whereas the **BUILT** file for v4.1-rc3-unstable contains:
```
Release: precise
Host: gomeisa
Start: 1431304568
[COLOR="#008000"]Debian: unstable
Configs: Ubuntu-4.0.0-1.1[/COLOR]
End: 1431308360
```

Possibly important changes are highlighted in green. The newer config is obvious. Apparently the **Debian: unstable** line is the reason the series shows as **unstable**. Can we assume from this that the kernels are built directly on Debian unstable rather than on Ubuntu Wily?

---

### Post by dino99 on 2015-06-26
rc2 is set to 'vivid' aka 'stable' as it is released
since rc3, 'vivid' have been replaced with 'instable' aka 'wily' as it is the ubuntu dev version

---

### Post by steveo314 on 2015-06-26
> **steveriley said:**
> I regularly install the newer kernels from the [Ubuntu kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). As described [in the wiki]("https://wiki.ubuntu.com/Kernel/MainlineBuilds"), the directories have typically been named in the format ***<tag>*-*<series>***. But starting with 4.1-RC3, the format has changed to ***<tag>*-unstable**. I've been running 4.1 since it appeared, and I'm not experiencing any instability.

The **BUILT** file for v4.1-rc2-vivid contains:
```
Release: precise
Host: gomeisa
Start: 1430710516
Debian: vivid
Configs: Ubuntu-3.19.0-16.16
End: 1430714261
```

Whereas the **BUILT** file for v4.1-rc3-unstable contains:
```
Release: precise
Host: gomeisa
Start: 1431304568
[COLOR="#008000"]Debian: unstable
Configs: Ubuntu-4.0.0-1.1[/COLOR]
End: 1431308360
```

Possibly important changes are highlighted in green. The newer config is obvious. Apparently the **Debian: unstable** line is the reason the series shows as **unstable**. Can we assume from this that the kernels are built directly on Debian unstable rather than on Ubuntu Wily?

A lot of Ubuntu's packages that go into the devel version come from the Debian experimental and unstable branches.

---

