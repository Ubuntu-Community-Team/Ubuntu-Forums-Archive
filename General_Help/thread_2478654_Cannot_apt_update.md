---
title: "Cannot apt update"
date: 2022-09-01
forum: General Help
---

### Post by avidseeker on 2022-09-01
Is ubuntu down?
I get the following when I try `sudo apt-get update` or `sudo apt update`

[https://i.imgur.com/Rcit08M.png](https://i.imgur.com/Rcit08M.png)

---

### Post by kc1di on 2022-09-01
Looks like your Server may be down. Update is working fine here. Try changing the server your using for ubuntu.

---

### Post by guiverc on 2022-09-01
Ubuntu 21.10 (*impish indri*) is EOL or ***End of Life***.

After a release goes EOL; it's archives are *moved*, and mirrors can *drop* support for the release.

Notice were posted, eg.

- [https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/](https://fridge.ubuntu.com/2022/07/19/ubuntu-21-10-impish-indri-end-of-life-reached-on-july-14-2022/)  on EOL
- [https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/](https://fridge.ubuntu.com/2022/06/01/ubuntu-21-10-impish-indri-reaches-end-of-life-on-july-14-2022/)  or *warning *six weeks before hand

and your system messages would have told you it too.

The EOL & warning notices gave instructions on upgrade (via link), though now it's EOL an extra step is required.

Refer [URL="https://help.ubuntu.com/community/EOLUpgrades"]https://help.ubuntu.com/community/EOLUpgrades

[/URL]> This is a follow-up to the End of Life warning sent earlier to  confirm that as of July 14, 2022, Ubuntu 21.10 is no longer supported.  No more package updates will be accepted to 21.10, and it will be  archived to old-releases.ubuntu.com in the coming weeks.


    The original End of Life warning follows, with upgrade instructions:


    Ubuntu announced its 21.10 (Impish Indri) release almost 9 months  ago, on October 14, 2021, and its support period is now nearing its end.  Ubuntu 21.10 will reach end of life on July 14, 2022.

[URL="https://help.ubuntu.com/community/EOLUpgrades"]
[/URL]

---

### Post by ActionParsnip on 2022-09-01
This is like looking for update for Windows 98. They don't exist

---

### Post by civilpolisen on 2022-09-01
Just do a simple  `sudo do-release-upgrade` and enjoy the upgrades from 22.04.

---

