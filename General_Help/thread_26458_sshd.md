---
title: "sshd"
date: 2005-04-13
forum: General Help
---

### Post by finkoisti on 2005-04-13
Hello,

I think ubuntu uses ssh2 as default protocol in ssh connection.
My work gateway supports only ssh1 so how to fix that in ubuntu?

---

### Post by heimo on 2005-04-13
This comes straight from my memory (can't verify the details), but should probably be enough. You can fix this globally on your system (for all users) by editing /etc/ssh/ssh_config and for the ssh server /etc/ssh/sshd_config (you should only need to edit the client part) - look for the line with *protocol* and number 2. If memory serves, you can change it to 1,2 or 2,1 to support also the older (less secure) protocol.

---

### Post by finkoisti on 2005-04-13
OK, thnx. Have to try it right when I go home. Hopefully it works...

---

### Post by finkoisti on 2005-04-13
It didn't work, it activates the ssh1 protocol but after that it needs that key file also for that..
So how to create those key files to ssh1 and ssh2

---

### Post by heimo on 2005-04-13
If you need to generate host key for SSH protocol 1, do:

```
ssh-keygen -t rsa1 -b 768 -f /etc/ssh/ssh_host_rsa1_key -N ""
```

And add it to sshd_config:
```
HostKey /etc/ssh/ssh_host_rsa1_key
```

---

