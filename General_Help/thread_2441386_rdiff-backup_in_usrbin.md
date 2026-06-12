---
title: "rdiff-backup in /usr/bin"
date: 2020-04-23
forum: General Help
---

### Post by Quarkrad on 2020-04-23
I have a backup.sh script in /usr/bin that runs a rdiff-backup process - It all works fine. At the moment the script is owned by the user; if the script were owned by root what difference would it make?  (Would all the folders/files backed up be owned by root?  Is there something relevant here re symbolic links being maintained during the rdiff-backup process)

---

### Post by Impavidus on 2020-04-23
You can set permissions such that only the owner can modify or execute the script and in that case the ownership matters. Otherwise, no difference. Except for SUID (set user ID) programs, programs run as the user invoking the program, not as the user owning the program.

It's generally a good idea if, for system-wide installed programs, only the root user can change the program.

BTW, the standards suggest that system-wide home-made scripts belong in /usr/local/bin.

---

### Post by Quarkrad on 2020-04-23
Thank you - at the moment I have my script in /usr/bin.  I will move it to ...local/bin

---

