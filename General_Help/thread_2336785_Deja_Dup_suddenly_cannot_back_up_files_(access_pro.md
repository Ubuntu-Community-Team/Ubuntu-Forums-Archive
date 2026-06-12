---
title: "Deja Dup suddenly cannot back up files (access problem)"
date: 2016-09-11
forum: General Help
---

### Post by VanillaMozilla on 2016-09-11
Running from an admin account, Deja Dup cannot back up files from other users. It also failed to back up one directory (/home/<myuser>/.config/nautilus-actions) from my own account (this may be a separate problem, as explained below).  It had no problem with the last backup (60 days ago), and there have been no changes in accounts or file ownership. The error message is
"Could not back up the following files. Please make sure you are able to open them."

As a matter of fact, I can only view the directories with sudo, so it appears to be an access problem. There is a bug report ( [https://bugs.launchpad.net/deja-dup/+bug/1313034](https://bugs.launchpad.net/deja-dup/+bug/1313034) ) about not backing up
/home/myuser/.cache/dconf
/home/myuser/.dbus and
/home/myuser/.gvfs,

but mine is a much broader problem. Changing ownership is clearly not the way to back up all users' files. Shouldn't deja dup handle other users' files without problem--especially since I'm running from admin? Is there a workaround? Is there a bug report?

Not backing up ~./.config/nautilus-actions/nautilus-actions.conf may be a separate, minor problem. I am the owner, but the access rules are "no list, create/delete, access". I'm not up on access rules and have to admit to being a tiny bit lazy, but huh? What gives? What is this "no list" and how did it get that way?

Running Ubuntu 14.04 LTS, fully patched.

---

