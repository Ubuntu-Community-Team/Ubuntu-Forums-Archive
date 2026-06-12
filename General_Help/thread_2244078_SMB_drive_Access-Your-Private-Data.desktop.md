---
title: "SMB drive: Access-Your-Private-Data.desktop"
date: 2014-09-13
forum: General Help
---

### Post by SchnappiJedi on 2014-09-13
Am using encrypted home folders. Before changing password could access home folder via SMB. Now get the "Access-Your-Private-Data.desktop" message. No need to run "ecryptfs-mount-private." Logging in locally or via SSH enables access to the home folder via SMB.

The problem is that want to access the home folder via SMB before logging in via SSH or locally (like it was before changing the password for the account in question).

So far have tried following these steps: [http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting](http://askubuntu.com/questions/115497/encrypted-home-directory-not-auto-mounting)

Any ideas?

---

### Post by cariboo on 2014-09-14
You may need to reset you smbpasswd to your new password:

```
smbpasswd -a
```

press Enter, and follow the prompts.

---

