---
title: "Problem running sshpass"
date: 2017-12-12
forum: General Help
---

### Post by satimis on 2017-12-12
Hi all,

Ubuntu 16.04 desktop

&#10219; apt-cache policy sshpass```

sshpass:
  Installed: 1.05-1
  Candidate: 1.05-1
  Version table:
 *** 1.05-1 500
        500 http://hk.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

```

&#10219; sudo sshpass -p 'mypasswd' ssh root@192.168.8.72```

ssh: connect to host 192.168.8.72 port 22: Connection refused

```

&#10219; sudo nano /etc/ssh/ssh_config 
adding```

PermitRootLogin yes

```
at the end

&#10219; service sshd restart```

Failed to restart sshd.service: Unit sshd.service not found.

```

Please help.  Thanks

satimis

---

