---
title: "Permission denied with ssh and hostname"
date: 2016-03-28
forum: General Help
---

### Post by joehc on 2016-03-28
[COLOR=#333333][FONT=Helvetica Neue]Hello[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]I've struggled with this for days now. I can't log into my raspberry pi (Xbian) via ssh from my computer. I try this:
[/FONT][/COLOR]```
ssh xbian@xxx.xxxxx.org[COLOR=#333333][FONT=Helvetica Neue]
[/FONT][/COLOR]
Permission denied (publickey).
```[COLOR=#333333][FONT=Helvetica Neue]
[/FONT][/COLOR]I use the service noip.com to get the hostname. 


I can however login via ssh when I use the internal IP. I have tried everything with change permissions, ports etc. but nothing seems to work. I'm missing something.


I've tried with the debug parameter:
```
ssh -vvv xbian@xxx.xxxxx.org
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /home/joe/.ssh/config
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxxxx.org [xx.xxx.xxx.xx] port 77.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/joe/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/joe/.ssh/id_rsa type 1
debug1: identity file /home/joe/.ssh/id_rsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/joe/.ssh/id_dsa" as a RSA1 public key
debug1: identity file /home/joe/.ssh/id_dsa type 2
debug1: identity file /home/joe/.ssh/id_dsa-cert type -1
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/joe/.ssh/id_ecdsa" as a RSA1 public key
debug1: identity file /home/joe/.ssh/id_ecdsa type 3
debug1: identity file /home/joe/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/joe/.ssh/id_ed25519 type -1
debug1: identity file /home/joe/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.6
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-4+deb7u3
debug1: match: OpenSSH_6.0p1 Debian-4+deb7u3 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug3: put_host_port: [xxx.xxxxx.org]:77
debug3: load_hostkeys: loading entries for host "[xxx.xxxxx.org]:77" from file "/home/joe/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/joe/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
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
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: setup hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: setup hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 7c:48:f3:87:2a:14:ea:39:f2:7d:fe:f5:7a:22:8b:74
debug3: put_host_port: [xx.xxx.xxx.xx]:77
debug3: put_host_port: [xxx.xxxxx.org]:77
debug3: load_hostkeys: loading entries for host "[xxx.xxxxx.org]:77" from file "/home/joe/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/joe/.ssh/known_hosts:2
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "[xx.xxx.xxx.xx]:77" from file "/home/joe/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/joe/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '[xxx.xxxxx.org]:77' is known and matches the ECDSA host key.
debug1: Found key in /home/joe/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/joe/.ssh/id_rsa (0x7f2b19da14d0),
debug2: key: /home/joe/.ssh/id_dsa (0x7f2b19da1560),
debug2: key: /home/joe/.ssh/id_ecdsa (0x7f2b19da1e90),
debug2: key: /home/joe/.ssh/id_ed25519 ((nil)),
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/joe/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering DSA public key: /home/joe/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Offering ECDSA public key: /home/joe/.ssh/id_ecdsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/joe/.ssh/id_ed25519
debug3: no such identity: /home/joe/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).
```
I get the errors if I use:
```
ssh-copy-id xbian@xxx.xxxxx.org
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
Permission denied (publickey).
```
[COLOR=#333333][FONT=Helvetica Neue]I have even tried to copy the id_rsa.pub key over manually and added to the keys, but I still get permission denied.[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Can someone pls help[/FONT][/COLOR]

[COLOR=#333333][FONT=Helvetica Neue]Thanks in advance[/FONT][/COLOR]

---

### Post by SeijiSensei on 2016-03-28
You need to copy id_rsa.pub from the client to the bottom of .ssh/authorized_keys.  Is that where you put it?

---

### Post by joehc on 2016-03-28
> **SeijiSensei said:**
> You need to copy id_rsa.pub from the client to the bottom of .ssh/authorized_keys.  Is that where you put it?
Yeah I did that. But isn't that also what
```
[COLOR=#000000][FONT=Ubuntu Mono]ssh-copy-id xbian@xxx.xxxxx.org[/FONT][/COLOR]
```
should do?

---

### Post by SeijiSensei on 2016-03-28
Yes, it does.  Are all the files in .ssh/ owned by your account?  Are they writable?  Look at "ls -al ~/.ssh".  Oh, and of course, ~/.ssh must be owned by you and should have at least 700 permissions.

---

