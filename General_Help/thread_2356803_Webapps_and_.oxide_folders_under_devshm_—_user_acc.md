---
title: "Webapps and .oxide folders under /dev/shm — user access rights"
date: 2017-03-27
forum: General Help
---

### Post by spazzeri on 2017-03-27
On Ubuntu 16.04.2 (with Unity desktop) there seems to be an issue with webapps for use by multiple users on the system.


  When userA is the first one to start the Gmail webapp after boot, a folder /dev/shm/Gmailmailgooglecom.oxide is created with mode 0700 and userA:userA as owner:group. When userB tries to start the same webapp in his profile, it fails with error messages about access rights to /dev/shm/Gmailmailgooglecom.oxide.


  Can anyone else reproduce the problem ? I doubt a single folder would  be used for all users by design, so I wonder if something specific to  my setup makes this happen.

---

