---
title: "delay for password prompt over ssh"
date: 2013-11-13
forum: General Help
---

### Post by magnus3 on 2013-11-13
When i try to ssh to a specific machine i always get 6 seconds delay before the password prompt appear. Debug below. I have tried with UseDNS no.

```

debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/username/.ssh/id_rsa ((nil))
debug2: key: /home/username/.ssh/id_dsa ((nil))
debug2: key: /home/username/.ssh/id_ecdsa ((nil))
[B]
IT PAUSES HERE FOR  6 SECONDS[/B]


debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/username/.ssh/id_rsa
debug3: no such identity: /home/username/.ssh/id_rsa
debug1: Trying private key: /home/username/.ssh/id_dsa
debug3: no such identity: /home/username/.ssh/id_dsa
debug1: Trying private key: /home/username/.ssh/id_ecdsa
debug3: no such identity: /home/username/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
username@192.168.69.150's password:

```

Any ideas?

---

### Post by Habitual on 2013-11-13
I had this issue also recently.
I changed the /etc/hosts entry 
from
127.0.0.1 localhost
to
```
#127.0.0.1 localhost
127.0.0.1 localhost.localdomain localhost
```

and it works without the delay I experienced. Reboot not required. The effect was *immediate*.

Hope that helps.

---

### Post by steeldriver on 2013-11-13
Another factor might be the gssapi auth methods - if you don't need to accept Windows domain based authentication you can try disabling those as well (in /etc/ssh/sshd_config)

---

### Post by magnus3 on 2013-11-13
When connecting from windows with putty that solved my problem! :) BUT when connecting from another ubuntu machine using ssh the problem still exists :(

---

### Post by magnus3 on 2013-11-13
No changes :(

---

### Post by Habitual on 2013-11-13
I should have specified the /etc/hosts on the server that seems slow to respond to the login, Sorry about that.

---

