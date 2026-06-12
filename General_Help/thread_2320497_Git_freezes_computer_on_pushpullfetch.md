---
title: "Git freezes computer on push/pull/fetch"
date: 2016-04-14
forum: General Help
---

### Post by SeanPatrickHagen on 2016-04-14
[COLOR=#111111][FONT=Ubuntu]It doesn't matter what repo, as soon as Git tries to do anything over the network it freezes my computer. Also, as soon as the computer freezes the syslog starts to fill with '^@'.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Doesn't matter if it's BitBucket, GitHub, or GitLab -- all of them have the same result.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm on Ubuntu 14.04, Linux 3.13.0-85-generic. Git version 2.8.1, installed via apt-get.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Git config settings:
[/FONT][/COLOR]
[FONT=courier new]push.default=matching
pull.rebase=true
sendpack.sideband=false[/FONT]

---

