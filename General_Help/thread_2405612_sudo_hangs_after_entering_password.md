---
title: "sudo hangs after entering password"
date: 2018-11-08
forum: General Help
---

### Post by FuturePilot on 2018-11-08
sudo has suddenly started hanging indefinitely after entering my password. I know exactly when it stopped working and during that time I had made no changes to the system. No changes were made to the system at least 12 hours prior to that even. I was copying some files with sudo in one window and opened another to run another sudo command which hung after the password. I didn't think too much of it because I was still able to use sudo in my first window due to the timeout grace period. But once that expired sudo was hanging in that instance too. There's nothing in the logs that would explain this around that time frame. I even rebooted the system but I still cannot use sudo. The system is 18.10

---

### Post by #&amp;thj^% on 2018-11-08
Yuck, and I'm "not"sure i can help with this but a stab in dark please show:
```
sudo -l 
[sudo] password for me: 
User me may run the following commands on me-pc:
    (ALL) ALL
    (ALL) ALL


```
Also this if possible:
```
type -a sudo
```
Should look like:
```

sudo is /usr/bin/sudo
sudo is /bin/sudo
```

---

