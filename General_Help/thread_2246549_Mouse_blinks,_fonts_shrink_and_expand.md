---
title: "Mouse blinks, fonts shrink and expand"
date: 2014-10-01
forum: General Help
---

### Post by PartisanEntity on 2014-10-01
I have a seriously strange problem.

Noticed it after updating. The mouse pointer is blinking, and all text is expanding and shrinking. Also, when I try click on the small cog icon and select shutdown, I get a log out option only and nothing happens when I click it.

Any ideas what it would be ?

---

### Post by PartisanEntity on 2014-10-02
I fixed it by creating a new user account, assigning it rights to use sudo, then logging into that new account, accessing my original home folder (of user 1) and moving all .* files into a backup folder.

Upon restarting and logging into user 1 the weird blinking stopped. I then had to manually migrate application configurations back to user 1 from the backup folder.

Seems some config file got corrupted.

---

