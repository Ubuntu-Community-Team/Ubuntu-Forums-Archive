---
title: "mount cifs doesnt work after password change"
date: 2018-05-28
forum: General Help
---

### Post by thecoded on 2018-05-28
Title, i have an oracle linux with a shared folder, that folder was mounted in one Ubuntu 14.04 Server. I changed the password of the user on the Oracle Linux and now i cant mount the shared folder, it says mount error 13 permission denied. I can ssh to the Oracle Linux with the new credentials, but mount doesnt work. Any tip??

I tried to restart the smb service on the oracle but it doesnt work


EDIT: Solved, i forgot about smbpasswd....

---

