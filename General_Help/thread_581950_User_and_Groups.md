---
title: "User and Groups"
date: 2007-10-19
forum: General Help
---

### Post by SteveF on 2007-10-19
I installed Gutsy.  A new option allows creating users from another found distribution.  Since I still had Feisty on another partition, this option was available.  So I selected the users, thinking this would save me time.

The problem I ran into was that the users had different IDs (most likely because they were created in a different order).  This caused a problem when mounting another partition the user created and now the IDs did not match.

So I thought I would change this, but IDs can't be changed on users (though they can on groups).  So I deleted the users and groups and created them manually in the right order to get the same ID.  But this would not cleanly work.  I kept getting group information for another user (though I removed those groups) and some users, when created, were not getting home folders created.  I couldn't get it straightened out.  It got to the point where the UI was behaving poorly.  I rebooted thinking that might help.  It didn't.

I ended up wiping out the install and reinstalling from scratch.  So I don't have an issue anymore, but I was wondering, Are there files I could have edited to clear this up?  It also looked like user and group information was cached somewhere because new groups created with the old IDs were getting the old group names.  Users were also not getting created correctly.  So I'm thinking it was cached or duplicated or shadowed somewhere and not getting cleared up.

Any suggestion?

Thanks,

Steve

---

