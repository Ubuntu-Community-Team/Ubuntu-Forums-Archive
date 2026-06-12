---
title: "Missing CPU system info when ssh in"
date: 2018-12-06
forum: General Help
---

### Post by NotQuiteSU on 2018-12-06
I have 2 diff ubuntu server systems. When I SSH into one, I get

> Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-138-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

  System information as of Thu Dec  6 22:19:25 EST 2018

  System load:    0.01               Processes:          203
  Usage of /home: 12.1% of 91.56GB   Users logged in:    0
  Memory usage:   30%                IP address for em1: 192.168.10.120
  Swap usage:     0%

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

63 packages can be updated.
5 updates are security updates.


My second system shows

> Welcome to Ubuntu 16.04.5 LTS (GNU/Linux 4.4.0-139-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

17 packages can be updated.
1 update is a security update.

New release '18.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


*** System restart required ***


How do I get the stats to show on the second system? (not sure how it happened on one, not the other

---

### Post by QIII on 2018-12-06
Hello!

Would you please post the results of 

```
dpkg -l | grep landscape
```

from the server that is not displaying the information?

---

