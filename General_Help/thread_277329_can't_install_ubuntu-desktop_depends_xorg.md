---
title: "can't install ubuntu-desktop depends: xorg"
date: 2006-10-14
forum: General Help
---

### Post by brandon moore on 2006-10-14
I think I am running Ubuntu 6.10 (edgy). Beryl is working well on my computer. However, when I run the update manager, it notifies me that I need to do a distribution upgrade. I go ahead with the distribution upgrade, but it tells me it cannot install ubuntu-desktop. I try to go into synaptic package manager to install ubuntu-desktop but it tells me it depends on xorg and can't install. How can I resolve this?

---

### Post by fanoodlehey on 2006-11-01
I have the same problem except with kubuntu-desktop. I wonder is it related to compiz?

---

### Post by Vevmesteren on 2007-01-28
same scenario as brandon on my end, I am googeling and surfing this forum, but have not found a solution as of yet. Kind of annoying as the update icon refuses to go away from my notification area. 

apt-get reutrns the following

```

[INDENT]sudo apt-get install ubuntu-desktopReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages
[/INDENT]
```

---

