---
title: "lubuntu - Mount Windows Share After Login"
date: 2013-03-22
forum: General Help
---

### Post by david.bell on 2013-03-22
I am using lubuntu 12.10 and likewise-open so that domain users can login. I am trying to figure out a way to have a Windows share mounted after a user logs in (with their domain account). I have found articles on permanently mounting a share, but that requires a config file with a set username/password. I am needing to mount the share using their current credentials (so that access to subfolders are controlled). If possible, i would like it to end up with a shortcut on the desktop as well.

Also, I'm not bookmarking it since I never know which users will be logging into which machines and we have way to many accounts to manually do them all.

---

### Post by steeldriver on 2013-03-22
You should be able to do it with [autofs]("https://help.ubuntu.com/community/Autofs") I think - I've only used it for nfs user shares myself so I can't help with the specifics of smb/cifs

---

### Post by david.bell on 2013-03-25
The only problem I see with that it is that it only mounts the file systems when they are accessed. I really need it to be constantly mounted. We have software that pulls from the share when you open it up.

---

### Post by humpty88 on 2013-04-19
How about a 'group' option in the fstab entry ? Valid users must be a member of the group.
A mount command could be added to each user's .profile.

---

