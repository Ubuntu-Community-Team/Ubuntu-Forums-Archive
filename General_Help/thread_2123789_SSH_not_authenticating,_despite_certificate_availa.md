---
title: "SSH not authenticating, despite certificate available"
date: 2013-03-08
forum: General Help
---

### Post by packetpenguin on 2013-03-08
Hi all.

I am new to SSH and trying to setup a SSH server and got it up and running, but have a problem with authentication.

I am SSHing in to localhost ('ssh localhost') and get:

> 
The authenticity of host 'localhost (::1)' can't be established.
ECDSA key fingerprint is 10:0d:c7:11:2f:b0:8f:31:e1:7a:48:b8:6e:21:93:b8.
Are you sure you want to continue connecting (yes/no)?


I don't think I should be getting this because I have copied '/etc/ssh/ssh_host_ecdsa_key.pub' into '~/.ssh/'.

Does anyone know why my client cannot authenticate the host?

---

### Post by packetpenguin on 2013-03-09
I tried putting the contents of 'ssh_host_ecdsa_key.pub' into '~/.ssh/known_hosts':

'cat ssh_host_ecdsa_key.pub > known_hosts'

... but it didn't solve the problem.


I also did a comparison in what the server sent me with the certificate, and the data differs:

ssh_host_ecdsa_key.pub:
> 
ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKG33ot2vCUSbEj95A3piw2GN72cH9rpJAxbBY/7aXMgDtvF/+ZHcJOLM4hj8o7PAKxqzSPU+B1EElKEm4CrsY0= root@a-D4


Host:
> 
|1|yAkd4kLo3ArLkClyPFUcTAn/3M8=|NjM4UHpiRFGuqatQdKOozUE7r7U= ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBKG33ot2vCUSbEj95A3piw2GN72cH9rpJAxbBY/7aXMgDtvF/+ZHcJOLM4hj8o7PAKxqzSPU+B1EElKEm4CrsY0=


I am not subject to a man-in-the-middle attack because these are the only two computers on my wired home LAN, but I don't like things not working on principal and would like to get this fixed.

---

### Post by steeldriver on 2013-03-09
Yes known_hosts is the place fo the host key(s) however I don't think you can just cat the host pubkey to ~/.ssh/known_hosts - it needs to be

hostname keytype key

Usually the file is hashed to obscure the hostname - as you can see in yours

It will only ask for that confirmation 1 time - and then will write the known_hosts entry for you so subsequent logins will recognise the host

IIRC you can use ssh-keygen -R hostname to remove a bad / out of date known_hosts entry

---

