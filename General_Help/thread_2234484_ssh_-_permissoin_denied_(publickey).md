---
title: "ssh - permissoin denied (publickey)"
date: 2014-07-15
forum: General Help
---

### Post by nos09 on 2014-07-15
hi, I am trying to setup a ssh key authentication. It works flawlessly on my local (virtualbox) ubuntu machine. But when i try to do the same with **exact same key** on my ubuntu machine hosted on 'DigitalOcean' with user 'git', it give the error permissoin denied (publickey) ! 

I have tried everything for ages .. it just doesn't seem to work !

BTW - i can access root account with pubkey(different pub key). I can access git user with password if i allow it.

can somebody help me out with this ?

---

### Post by nerdtron on 2014-07-15
Give it a try.
On the digital ocean server.
1. Login as git.
2. Generate ssh key for user git using ssh-keygen.
3. Copy the generated public key of the user git to your local computer.

On you local computer.
1. Use the public you just copied using the syntax: ssh -i /path/to/pub.key git@IPofServerinDigitalOcean

---

### Post by Lars Noodén on 2014-07-15
> **nerdtron said:**
> 3. Copy the generated public key of the user git to your local computer.


Isn't that backwards?  The private key goes on the local computer and the public key goes on the server, usually.

---

### Post by nos09 on 2014-07-15
> **nerdtron said:**
> Give it a try.
On the digital ocean server.
1. Login as git.
2. Generate ssh key for user git using ssh-keygen.
3. Copy the generated public key of the user git to your local computer.

On you local computer.
1. Use the public you just copied using the syntax: ssh -i /path/to/pub.key git@IPofServerinDigitalOcean

Here is what I tried. 

ON Git-server:

generated keygen using 

```
ssh-keygen -t rsa -C "git@IPofServerinDigitalOcean"

```
added the id_rsa.git to > authorized_keys in .ssh/

copied the .pub key to my local machine - using scp.


used the ssh -i .pub git@IPofServerinDigitalOcean but I still got permission denied (publickey) error.

So did the other way tooo ... added the pubkey too into authorized_key file.. and tired to login as private key tooo but with no luck !


How is this possible ?!?!

do you want me to post out put of ssh -vvv ?? and sshd_config of server ? of both try of pub.key or private key ?

---

### Post by Lars Noodén on 2014-07-15
The output of ssh -vvv might help, at least the parts where it is authenticating, where the public key is on the remote server and the private key is on the local server.  

Have you tried adding *-o IdentitiesOnly=yes* into the mix?  There is a bug on some versions of Ubuntu where keys get snarfed up by the agent and tried in preference to the one specified in the runtime options.  Then after automated 6 fails (default), the overall login fails.

---

### Post by nos09 on 2014-07-15
> **Lars Noodén said:**
> The output of ssh -vvv might help, at least the parts where it is authenticating, where the public key is on the remote server and the private key is on the local server.  

Have you tried adding *-o IdentitiesOnly=yes* into the mix?  There is a bug on some versions of Ubuntu where keys get snarfed up by the agent and tried in preference to the one specified in the runtime options.  Then after automated 6 fails (default), the overall login fails.

```
[x@arch .ssh]$ ssh -i id_rsa.git -vvv git@git-server.com 
OpenSSH_6.6.1, OpenSSL 1.0.1h 5 Jun 2014
debug1: Reading configuration data /home/x/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to git-server.com [IPOFREMOTEMAC] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "id_rsa.git" as a RSA1 public key
debug1: identity file id_rsa.git type 1
debug1: identity file id_rsa.git-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6p1 Ubuntu-2ubuntu1
debug1: match: OpenSSH_6.6p1 Ubuntu-2ubuntu1 pat OpenSSH_6.5*,OpenSSH_6.6* compat 0x14000000
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "git-server.com" from file "/home/x/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/x/.ssh/known_hosts:13
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug2: compat_kex_proposal: original KEX proposal: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: Compat: skipping algorithm "curve25519-sha256@libssh.org"
debug2: compat_kex_proposal: compat KEX proposal: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-dss-cert-v00@openssh.com,ssh-ed25519,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: setup hmac-md5-etm@openssh.com
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug2: mac_setup: setup hmac-md5-etm@openssh.com
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 13:34:b3:df:14:90:ce:ea:13:46:e9:7e:f5:a6:3d:6f
debug3: load_hostkeys: loading entries for host "git-server.com" from file "/home/x/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/x/.ssh/known_hosts:13
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "IPOFREMOTEMAC" from file "/home/x/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/x/.ssh/known_hosts:11
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'git-server.com' is known and matches the ECDSA host key.
debug1: Found key in /home/x/.ssh/known_hosts:13
debug1: ssh_ecdsa_verify: signature correct
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
debug2: key: id_rsa.git (0x7f59fc3d8ea0), explicit
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: id_rsa.git
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

```

> Have you tried adding *-o IdentitiesOnly=yes* into the mix?  There is a bug on some versions of Ubuntu where keys get snarfed up by the agent and tried in preference to the one specified in the runtime options.  Then after automated 6 fails (default), the overall login fails.

I didn't get what were you trying to say there.. except its a but in ubuntu.

both publick key and private key are added in authorized_key file on git-server. (just in case ...)

---

### Post by Lars Noodén on 2014-07-15
The key appears to be no good and RSA1 is outdated.  

```

debug3: Incorrect RSA1 identifier
debug3: Could not load "id_rsa.git" as a RSA1 public key

```

You could use RSA or even Ed25519 

Best to remove the bad key from your local host and from ~/.ssh/authorized_keys on git-server.com

Then generate new keys.

```

cd ~/.ssh/
ssh-keygen -t rsa -b 4096 -f id_rsa.git

```

Then use ssh-copy-id to transfer the key over to the remote server.

---

### Post by nos09 on 2014-07-15
Right on the spot !! man you are genius .. 

btw if i use this command again to add another keys will authorized_key file will be overwritten ? I want to give different people different keys ..

---

### Post by Lars Noodén on 2014-07-16
ssh-copy-id can be used to copy multiple keys.  I think it even checks to see if the key is already copied or not so as to avoid duplicates.  It is a shell script so it is rather easy to read what it tries to do:

```

 less /usr/bin/ssh-copy-id

```

When you create the keys it is also a good idea to add a comment with a **-C**.  I forgot to add that in the example above.  However, a comment can be added after the fact by editing the public key and adding your comment at the end of the line.  Just be sure that the key stays on a single line.

---

