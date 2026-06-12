---
title: "SCP as root"
date: 2007-04-11
forum: General Help
---

### Post by kooseefoo on 2007-04-11
Okay, I recently became acquainted with the scp command, used to copy files over an ssh connection.

Here's my question: what if I need root access to get to the file, but the only way to become root on my system is with a sudo command?


Thanks,
Chris

---

### Post by 56seeker on 2007-07-13
I think you'd be OK if you start scp with sudo. It should set the rights for the session

---

### Post by mpeters on 2007-07-13
> **kooseefoo said:**
> Okay, I recently became acquainted with the scp command, used to copy files over an ssh connection.

Here's my question: what if I need root access to get to the file, but the only way to become root on my system is with a sudo command?


Thanks,
Chris

```
sudo scp myfile 1.2.3.4:/home/me/
```

will copy the file with root access on the **local** machine, this will then prompt you for **root**'s password on the **remote** machine. sudo will not give you root access on the remote machine unless you know root's password. In order to copy as another user to the other machine you need to do:

```
sudo scp myfile username@1.2.3.4:/home/
```

---

