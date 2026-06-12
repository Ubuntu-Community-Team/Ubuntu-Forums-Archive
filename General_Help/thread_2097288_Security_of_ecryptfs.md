---
title: "Security of ecryptfs"
date: 2012-12-22
forum: General Help
---

### Post by Sworddragon on 2012-12-22
I'm thinking about a few things of ecryptfs which may be a problem:

[list][*]The file ~/.ecryptfs/wrapped-passphrase is readable even if I'm not logged in. Can an attacker do something just with the content of this file?
[*]Does ecryptfs overwrite the key in the memory after I'm logging out to prevent a cold boot attack?
[*]The faq on Sourceforge says there is no filename encryption but a ticket on Launchpad says it is already implemented. Can somebody confirm this?[/list]

---

