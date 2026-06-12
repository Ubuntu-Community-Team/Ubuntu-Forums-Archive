---
title: "Broken? Partitions"
date: 2007-04-19
forum: General Help
---

### Post by mrmadowl on 2007-04-19
So a dual booting PC with Linux Ubuntu (was Dapper, but upgraded to Edgy) and XP. Ubuntu is on its own 100GB(hdb) Hard drive and windows is on its own also (hda). My problem is after I upgraded to Edgy, Ubunut keeps telling me 100% of my HD is FULL! XD When i check the sizes using the extfs driver (for windows) in win explorer and it says my HD is only 20GB. When I go to adminastrative tools in windows it detects 2 partitions on linux (the root and the swap), however they are the correct sizes, 500MB and like 100GB. When I am in Ubuntu it says the partition is 100GB and that I have 99GB used, i know that is impossible! It looks as if the partition is being scaled down according to how much info is on it, if I delete things, that becomes the new size. So I think it might be something to do with how it crashed during the upgrade to Edgy, possibly damaging the partition table on my second HD, not sure though. I would just reinstall it, but I've got a nice setup with my WLAN card (took forever to setup) and my beautiful Beryl and am hoping to salvage it. ANY SUGGESTIONS ? XD

oh also I looked in the disk manager on the livecd and it showed 2 extra partitions that seem to be hidden, possibly used to upgrade to Edgy, one was like /etc/ and the other was /tmp/...i know those are directories in the root fs but thought it was kinda funny to have "hidden" partitions that only appeared in the disk manager (now unsupported in Edgy), possibly incomplete partitions or something that were not removed because of the crash. I should probably be on an Ubuntu forum, but the damage has been done here so i figure its worth a try, mabey someone has encountered it.

---

