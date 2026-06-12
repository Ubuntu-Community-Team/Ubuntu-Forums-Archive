---
title: "Ubuntu 14.04 LTS can't create an account or remove one"
date: 2015-07-26
forum: General Help
---

### Post by chris382 on 2015-07-26
When trying to create an account in the settings i get this error "Failed to delete user" "running '/usr/sbin/userdel' failed: Child process exited with code 8"
I've also tried to create an account in the Terminal but it gives me an error "useradd: existing lock file /etc/subuid.lock without a PIDuseradd: cannot lock /etc/subuid; try again later."
What is some stuff i can try to maybe fix this? Thankyou.

---

### Post by Vladlenin5000 on 2015-07-26
So you were in System Settings > User accounts, unlocked it, pressed "+" to add a new user account and then got an error message about deleting an user, without you actually telling it to delete some other user?
BTW, *useradd* or *adduser* require *sudo.*

---

### Post by chris382 on 2015-07-26
No, that's not correct. I'm trying to remove an account. When i try to create an account in System Settings > User accounts, it gives me the error [COLOR=#000000]"Failed to delete user" "running '/usr/sbin/userdel' failed: Child process exited with code 8"
[/COLOR]I've tried using sudo with useradd already.
Thanks.

---

### Post by Vladlenin5000 on 2015-07-26
Does _your_ user has *sudo* privileges?

Anyway, it doesn't make sense that error message [in the User Accounts GUI] when you try to _create_ a new account.
It would make sense when trying to _delete_. The error code 8 means the user you're trying to delete is still logged on and/or has processes running.

---

### Post by chris382 on 2015-07-26
Yes my user has sudo privileges. When trying to create an account it gives me the error "running '/usr/sbin/adduser' failed: Child process exited with code 1"

---

### Post by sandyd on 2015-07-26
Hi, can you follow these steps:

1. Reboot
2. On reaching the login screen, login, and do not open anything.
3. Open the terminal
4. Run the following ```

ls -l /etc/subgid.lock

```
5. If there is a file, run
```

sudo rm /etc/subgid.lock
```
6. Try adding the file again

---

### Post by chris382 on 2015-07-27
Thanks sandyd. I've removed the file and now when i try add a user in terminal it says "useradd: existing lock file /etc/subuid.lock without a PIDuseradd: cannot lock /etc/subuid; try again later."
"adduser: `/usr/sbin/useradd -d /home/heee -g heee -s /bin/bash -u 1002 heee' returned error code 16. Exiting."

---

