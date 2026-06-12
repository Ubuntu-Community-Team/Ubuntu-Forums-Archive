---
title: "Messed up my SSH settings?"
date: 2015-03-13
forum: General Help
---

### Post by sebastian16 on 2015-03-13
Hi,

I have a problem with my SSH login to a server at work. I always get the following error message:

```
ssh_exchange_identification: read: Connection reset by peer
```

Everything worked before I did the following due to being stupid: I created another SSH key pair for using git / GitHub, as follows:

```
ssh-keygen -t rsa -C benutzer@email.com
Generating public/private rsa key pair.
Enter file in which to save the key (/home/XXX/.ssh/id_rsa): /home/XXX/.ssh/id_rsaGIT
```

Now the following files exist in /.ssh:

```
id_rsa  id_rsaGIT  id_rsaGIT.pub  id_rsa.pub  known_hosts  known_hosts.old

```

And when trying to log onto the server via ssh myname@server -vv, I get

```
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [XX.XX.XX.XX] port 22.
debug1: Connection established.
debug1: identity file /home/XXX/.ssh/id_rsa type 1
debug1: identity file /home/XXX/.ssh/id_rsa-cert type -1
debug1: identity file /home/XXX/.ssh/id_dsa type -1
debug1: identity file /home/XXX/.ssh/id_dsa-cert type -1
debug1: identity file /home/XXX/.ssh/id_ecdsa type -1
debug1: identity file /home/XXX/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/XXX/.ssh/id_ed25519 type -1
debug1: identity file /home/XXX/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
ssh_exchange_identification: read: Connection reset by peer

```

What has happened, and how can I fix it? 

Please reply detailed, I am not experienced with SSH.

---

