---
title: "Cant connect from xp to edgy with ssh and rsa"
date: 2006-11-07
forum: General Help
---

### Post by andyrobo60 on 2006-11-07
I upgraded (with clean install) to edgy 2 weeks ago and I have not been able to get ssh working since. I installed ssh and used ssh-keygen to make the the rsa files. 

I copy id_rsa over to my laptop (running xp) and use puttygen to make in a .ppk file and select it in putty > Auth but when I try to connect I always get "Server refused our key". 

I can connect OK using my password.

this is my sshd_config
```

Port 22
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin no
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	%h/.ssh/authorized_keys
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes 

```

could someone please help.

---

