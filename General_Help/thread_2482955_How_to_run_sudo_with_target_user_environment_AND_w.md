---
title: "How to run sudo with target user environment AND without password prompt"
date: 2023-01-15
forum: General Help
---

### Post by batemanjjj on 2023-01-15
Hi,

```
root@Test:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:        20.04
Codename:       focal
root@Test:~#

```


I'm user1 and need to run a script as user2 and there must NOT be any password prompt.
Added below line to sudoers (using visudo of course)

```
user1 ALL=(user2) NOPASSWD: /usr/local/bin/script.sh
```

and then I ran the below command as user1
```
sudo -u user2 /usr/local/bin/script.sh
```

it runs but a part of actual execution fails becoz of user2 's environment is NOT set.
Hence tried below -

```
sudo -i -u user2 /usr/local/bin/script.sh
```

But it asks for the password, if I type in the password then the script runs just fine but the problem is that it prompts for password which is a problem for automation. So my query is how could I run sudo -i without password prompt.

My setup:
```
root@Test:~# egrep "^[^#]|^#include" /etc/sudoers
Defaults env_reset
Defaults mail_badpass
Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
root ALL=(ALL:ALL) ALL
%admin ALL=(ALL) ALL
%sudo ALL=(ALL) NOPASSWD: ALL
user1 ALL=(user2) NOPASSWD: /usr/local/bin/script.sh
#includedir /etc/sudoers.d
root@Test:~#
root@Test:~# ls /etc/sudoers.d
README
root@Test:~#

```

Looks like setting the target user's ENV variables in the script itself is the only option but updating script is my last option, hence looking for a better/alt solution.

Appreciate any help :slight_smile:

---

### Post by batemanjjj on 2023-01-16
Got help from others and the solution is 
> user1 ALL=(user2) NOPASSWD: /bin/bash -c /usr/local/bin/script.sh

---

