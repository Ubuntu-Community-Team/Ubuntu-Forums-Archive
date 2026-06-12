---
title: "Adding and using second user causes system lockup"
date: 2008-04-07
forum: General Help
---

### Post by seldomvisitor on 2008-04-07
Using standard GUI admin tool to add users, Added a secondary non-admin user. Then attempted to log in as that user and use it - this caused a total system lockup requiring manual hard reset. Any attempts to use secondary user lock up system.

The display behavior right after login was somewhat different from the display behavior after logging in as the initial (admin-capable) user - icon bars appearing and disappearing, for example. Otherwise all appears "normal" visually and, for example, audibly..

Started up a terminal right after logging in as the secondary user - typed in "ps -ef" and got what appears to be MOST of the "ps" output before the system froze.

Started up firefox right after logging in ad the secondary user - firefox started, did not get out to network before system lockup (black background for firefox display).

---------

That's about it - the installation of Gutsy is as virgin as I could make it - downloaded a CD image, burned it to a CD, used that to bootstrap this machine into a working UBUNTU install, then had-editted a couple network-related files to get wireless networking working (available GUI method didn't allow WEP setup correctly, etc).. Used and updated that install quite a bit as original user.

So has anyone got a clue what's going on here? I fear hidden permission problems, of course, since all seems to work fine as original user but not at all as a secondary user.

BTW - 600MHz PIII with a Gbyte of RAM, lots of disk space, ATI Radeon video, maybe Soundblaster audio, Linksys wireless card.

---

