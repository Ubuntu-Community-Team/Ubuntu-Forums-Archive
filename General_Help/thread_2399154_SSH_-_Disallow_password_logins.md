---
title: "SSH - Disallow password logins"
date: 2018-08-22
forum: General Help
---

### Post by esclavosoy on 2018-08-22
Hello,

I'm trying to set ssh to disallow password logins.  I've made some changes to my ssh_config file but it doesn't seem to affect it.  I've also have restarted the daemon with no avail.

Here's my config file:
```
Host *#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
    PasswordAuthentication no
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    PubkeyAuthentication yes
```

After I made the changes I ran:
```
sudo systemctl reload sshd
```

Hope you can help.

TIA

---

### Post by steeldriver on 2018-08-22
It looks like you edited the ssh_config (SSH client configuration) file - to change  features of the *server*, you need to edit the ssh**d**_config file

---

### Post by esclavosoy on 2018-08-22
Cool, thanks for catching that.  I'm all good now.

---

