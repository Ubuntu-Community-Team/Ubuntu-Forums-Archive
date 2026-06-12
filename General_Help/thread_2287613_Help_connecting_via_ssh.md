---
title: "Help connecting via ssh"
date: 2015-07-20
forum: General Help
---

### Post by jacebennest on 2015-07-20
Hi there, having some issues connecting to my ubuntu server through ssh. 

I used to be able to do it, but recently wiped my old server and put on a fresh install. But now I can't connect.

In my google searching, it seems like I need new keys or something, I can't really tell how to make them or update them... any help would be appreciated!

ssh me@server -v outputs ```
OpenSSH_6.2p2, OSSLShim 0.9.8r 8 Dec 2011
debug1: Reading configuration data /etc/ssh_config
debug1: /etc/ssh_config line 20: Applying options for *
debug1: Connecting to 10.0.0.3 [10.0.0.3] port 22.
debug1: Connection established.
debug1: identity file /Users/me/.ssh/id_rsa type -1
debug1: identity file /Users/me/.ssh/id_rsa-cert type -1
debug1: identity file /Users/me/.ssh/id_dsa type -1
debug1: identity file /Users/me/.ssh/id_dsa-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH*
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 88:9a:d4:6b:a4:28:41:df:ff:39:87:7d:c8:63:15:bf
debug1: Host '10.0.0.3' is known and matches the RSA host key.
debug1: Found key in /Users/me/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/me/.ssh/id_rsa
debug1: Trying private key: /Users/me/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey).
```

---

### Post by QIII on 2015-07-21
Have a look [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") and see if you've missed something in generating and distributing keys.

And then have a read through [this]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").

That's probably all clear as mud, so don't hesitate to come back and ask more questions!

Cheers.

---

### Post by jacebennest on 2015-08-01
Fixed it. The issue was that my server did not have my public key in the authorized_keys file.

The problem I was having was finding my public key on my Macbook. Public keys should be stored in ~/.ssh/id_rsa.pub. Just copy the contents into the server at ~/.ssh/authorized_keys. Should look similar this:

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCxa8nEaldPXyRm+8z/fennO5w0wK9zdqITjZ+FYdZoD298QdqMTcg/nfJ5kz4ihSfxUbBlgKB9sewki1zSgREhZADFJLFjsdlsstCGf5q0yg6RxWp6QU7T/teNlQCYEl+1FMuSoP8BvtagFFd1/FWVttSB27NH3gGhiLcbDrWNJR6Z2sdalasd9a332apoqqyCLk0Dv5OUuXiRvVj5yH0uqeBBNPkpF+BgLJyXu1ZWaMZWjr15lZXZgC7UTiV2/WCS85umQnS7mxp6plQT7WLbL6RQF0bb230Tpm2YV+KW9McqG3cS08xPwvV2hW+35GUb29X9LzQcUSFB [email]USER@USERMacBook.local[/email]

---

### Post by SeijiSensei on 2015-08-01
Actually there is an easier method, at least on Linux, but probably available on Macs as well.  Use the ssh-copy-id command like this:
```
ssh-copy-id user@remote
```
You'll need to have permission to log into the remote as "user" this one time.  After that it will use the key to authenticate.

---

