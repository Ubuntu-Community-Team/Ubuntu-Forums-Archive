---
title: "Is package orphaning procedure available like in Debian?"
date: 2013-09-11
forum: General Help
---

### Post by aleks2 on 2013-09-11
I see [some projects]("https://launchpad.net/wiithon") have no activity for years. Is there a standard mechanism to make them [orphaned]("http://www.debian.org/devel/wnpp/orphaned") like in Debian?

---

### Post by ian-weisser on 2013-09-11
Your question is mixing up two concepts: Upstream development vs package maintainership within a distribution.

The Launchpad example is an abandoned upstream project. Some other developer can come along and resurrect the project, or fork the code into their new project, and package it for any distro they wish. Notice that the Launchpad example hasn't had a package since 2009. It's not in Ubuntu at all. If it were in Debian, the project wouldn't be on the WNPP list (though a package downstreamed from the project may).
 
The WNPP page lists packages that the distro maintainer has abandoned, and are eligible for re-adoption by a new maintainer. Maintainers are usually not the upstream developer, but instead the liason between the distro and the upstream. Ubuntu has no comparable list to WNPP since maintainership is done differently in Ubuntu. Many Debian maintainers are individuals, some are teams (like the debian games team). In Ubuntu, nearly all are teams.

---

