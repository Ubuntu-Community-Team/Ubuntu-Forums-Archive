---
title: "[SOLVED] SSH login banner - Help needed."
date: 2007-09-20
forum: General Help
---

### Post by battletux on 2007-09-20
Hi,

I'm looking for some help in setting up an SSH login banner, the one that appears before you login.

I've setup up the MOTD for after you login and it is fine.

I have added the

```
Banner /etc/issue.net
```

line to my /etc/ssh/ssh_config file but when I restart sshd and try to login with 

```
ssh user@<external IP>
```

I get the following error:

> 
/etc/ssh/ssh_config: line 49: Bad configuration option: Banner
/etc/ssh/ssh_config: terminating, 1 bad configuration options


and ssh wont accept any incoming connection until I remove the line.

I have checked the ssh_config man page and can see nothing relating to a Banner command even though I have read about it after a quick google search.

Can anyone point me in the right direction for having this work?

I'm running Ubuntu 7.04 (fiesty).

Thanks in advance.

---

### Post by battletux on 2007-09-20
Fixed it.

I needed to edit /etc/ssh/sshd_config NOT /etc/ssh/ssh_config

---

