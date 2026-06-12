---
title: "How to restart ssh service in kubuntu 18"
date: 2019-09-23
forum: General Help
---

### Post by petrogromovo on 2019-09-23
Hello,
How to restart ssh service in kubuntu 18(that is personal laptop)
In next I found several decisions, but all gave error :
```
$ ps -ef | grep sshd
serge    24891 24553  0 10:30 pts/3    00:00:00 grep --color=auto sshd
$ /usr/sbin/sshd -D
bash: /usr/sbin/sshd: No such file or directory
$ /usr/bin/sshd -D
bash: /usr/bin/sshd: No such file or directory
$ sudo /etc/init.d/ssh start
sudo: /etc/init.d/ssh: command not found
$ sudo start ssh
sudo: start: command not found
$ sudo systemctl restart ssh
Failed to restart ssh.service: Unit ssh.service not found.
$ sudo service ssh restart
Failed to restart ssh.service: Unit ssh.service not found.
$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 18.04.3 LTS
4.15.0-20-generic
x86_64

```
Thanks!

---

### Post by The Cog on 2019-09-23
systemctl should recognise both ssh and sshd as service names. Are you sure ssh is installed? sudo apt install openssh-server.

---

