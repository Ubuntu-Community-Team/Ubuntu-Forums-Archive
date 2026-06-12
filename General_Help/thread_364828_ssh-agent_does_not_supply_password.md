---
title: "ssh-agent does not supply password"
date: 2007-02-18
forum: General Help
---

### Post by butterman on 2007-02-18
I can use ssh to login with a password.  I want to ssh-agent to supply the password but--after many hours--I cannot get it configured correctly.  I followed these steps:

1. eval `ssh-agent`

2. ssh-add

What does this mean: "we sent a publickey packet, wait for reply"?  It seems that the localmachine never received the private key from the remotemachine.  Why?

```
OpenSSH_4.2p1 Debian-7ubuntu3.1, OpenSSL 0.9.8a 11 Oct 2005
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to atlas [192.168.1.101] port 22.
debug1: Connection established.
debug1: identity file /home/rsmith/.ssh/identity type 0
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/rsmith/.ssh/id_rsa type 1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/rsmith/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.2p1 Debian-7ubuntu3.1
debug1: match: OpenSSH_4.2p1 Debian-7ubuntu3.1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.2p1 Debian-7ubuntu3.1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 516/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'atlas' is known and matches the RSA host key.
debug1: Found key in /home/rsmith/.ssh/known_hosts:6
debug2: bits set: 490/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/rsmith/.ssh/id_rsa (0x80914b8)
debug2: key: /home/rsmith/.ssh/id_dsa (0x80914d0)
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/rsmith/.ssh/id_rsa
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /home/rsmith/.ssh/id_dsa
debug2: **we sent a publickey packet, wait for reply**
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
```

---

### Post by WW on 2007-02-18
Have you added your public key to ~/.ssh/authorized_keys on the remote computer?  (I don't know enough about this stuff to know from the log you posted if that is the problem; I'm just guessing at something that might be wrong.)  Here is one way you can do it (only do this once) (EDIT: See the post by Co.Sinecure below for an easier way):
> $ cat ~/.ssh/id_dsa.pub | ssh [email]userid@remote.computer.com[/email]  'cat - >> ~/.ssh/authorized_keys'
That will append your local id_dsa.pub to the authorized_keys file on the remote computer.

---

### Post by butterman on 2007-02-19
I have already appended my public keys to authorized_keys.  Just to be sure, I executed the command you suggested, started ssh-agent, and associated the key with ssh-add (which acknowledged the key and asked for my passphrase), but ssh still asks for my password.  I'm assuming that because I can use ssh with a password, that my public key has been properly distributed to the remote computer.

---

### Post by Co.Sinecure on 2007-03-07
> **WW said:**
> Have you added your public key to ~/.ssh/authorized_keys on the remote computer?  (I don't know enough about this stuff to know from the log you posted if that is the problem; I'm just guessing at something that might be wrong.)  Here is one way you can do it (only do this once):

That will append your local id_dsa.pub to the authorized_keys file on the remote computer.

There is a much easier way to achieve this:
```
ssh-copy-id -i .ssh/id_rsa.pub user@domain
```

It will ask you to log in normally with your password, and from then on you should be able to log in with your passphrase.

---

### Post by WW on 2007-03-07
That is nicer.  Thanks for the tip!

---

### Post by butterman on 2007-03-10
That's pretty slick.  I still can't login without a password.  I've been working on this problem, literally, for months.  Anybody know what's wrong?

---

### Post by fphsml on 2007-05-25
I was confused at first too. After having read your post, I googled up this

[http://www.noah.org/wiki/index.php/Howto_ssh_public_keys#Older_notes](http://www.noah.org/wiki/index.php/Howto_ssh_public_keys#Older_notes)

Yes. Just use the "Older Notes" section. I was up and running in a minute without a password.

---

### Post by butterman on 2007-05-25
I followed the steps under Older Notes, as you suggested, but without success:

1. created a public key with no passphrase:

```
ssh-keygen -t rsa
```

2. Copied the public key to the remote server.

```
scp ~/.ssh/id_rsa.pub user@remote.example.com:/tmp/id_rsa.pub
```

3. On the remote server, I appended the new public key.  I already had a .ssh directory but made sure the permissions were set to 700.

```
cat /tmp/id_rsa.pub >> ~/.ssh/authorized_keys
```

4. ssh still asks for a password

```
ssh user@remote.example.com
```

I guess this is saying that if I don't enter a passphrase, I don't need ssh-agent.  It funny because for most users this "just works."  I must have some residual setting that is preventing this from working.  I wish I could just start over.  I tried overwriting the authorized_keys file but that didn't help.  Any thoughts would be appreciated.

---

### Post by WW on 2007-05-25
I'm not sure if this is the problem, but did you run ssh-add after ssh-keygen?

---

### Post by fanatik on 2007-05-25
can you log into any other remote systems passwordlessly? if not then its a problem on your box, if yes then its a problem with the remote box. if this is your 1st and only attempt then we need to look at everything. it's probably permissions. can you give the output of:

```
$ ls -ld ~/.ssh
$ ls -l ~/.ssh
$ ls -ld ~
```

on both your machine and the remote machine.

also if the remote box is also one you control, you might want to take a look at /etc/ssh/sshd_config just to make sure that PubkeyAuthentication isn't set to no! :)

---

### Post by butterman on 2007-05-28
```
can you log into any other remote systems passwordlessly?
```

Yes.  Initially I didn't realize that when public key authentication works, it should request a passphrase, not the user's password.  So, the problem is not with ssh-agent at all.  The problem is that I cannot log in to the remote machine using public key authentication, either remotely or at the console.

```
rsmith@atlas:~/.ssh$ grep Pubkey /etc/ssh/sshd_config
PubkeyAuthentication yes
```

From the remote machine:

```
rsmith@atlas:~/.ssh$ ls -ld ~/.ssh
drwx------ 2 rsmith rsmith 4096 2007-03-10 14:35 /home/rsmith/.ssh
rsmith@atlas:~/.ssh$ ls -l ~/.ssh
total 52
-rw------- 1 rsmith rsmith  5570 2007-05-28 13:23 authorized_keys
-rw------- 1 rsmith rsmith 11204 2007-05-28 13:23 authorized_keys2
-rw------- 1 rsmith rsmith  1508 2007-03-10 14:33 authorized_keys.sav
-rw------- 1 rsmith rsmith  1192 2007-05-28 13:23 id_dsa
-rw------- 1 rsmith rsmith  1114 2007-05-28 13:23 id_dsa.pub
-rw------- 1 rsmith rsmith   639 2007-02-18 17:57 identity.pub
-rw------- 1 rsmith rsmith  1675 2007-02-17 14:11 id_rsa
-rw------- 1 rsmith rsmith   394 2007-02-18 17:58 id_rsa.pub
-rw------- 1 rsmith rsmith  2601 2007-05-28 12:58 known_hosts
-rw------- 1 rsmith rsmith  1114 2007-05-28 12:45 rhino.pub
rsmith@atlas:~/.ssh$ ls -ld ~
drwxr-xr-x 49 rsmith rsmith 4096 2007-05-28 12:30 /home/rsmith

```

```
 ssh -v -v -v localhost
.
.
.
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rsmith/.ssh/identity
debug3: no such identity: /home/rsmith/.ssh/identity
debug1: Offering public key: /home/rsmith/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Offering public key: /home/rsmith/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
rsmith@localhost's password:

```

---

### Post by fanatik on 2007-05-29
so even trying sshing locally doesnt work!? since permissions look good, i'd suggest moving authorized_keys(& 2) to one side and re-creating authorized_keys by cat ing id_dsa.pub into it, ie they should be identical, and then making sure permissions are correct. there's no reason it shouldn't work.

---

### Post by butterman on 2007-05-29
I followed your suggestions, but ssh still asks for my password rather than the passphrase.

```
rsmith@atlas:~/.ssh$ ls -l
total 56
-rw------- 1 rsmith rsmith  1114 2007-05-29 20:09 authorized_keys
-rw-r--r-- 1 rsmith rsmith  1114 2007-05-29 20:14 authorized_keys2
-rw------- 1 rsmith rsmith 11204 2007-05-28 13:23 authorized_keys2.sav
-rw------- 1 rsmith rsmith  5570 2007-05-28 13:23 authorized_keys.sav
-rw------- 1 rsmith rsmith  1264 2007-05-29 20:09 id_dsa
-rw------- 1 rsmith rsmith  1114 2007-05-29 20:09 id_dsa.pub
-rw------- 1 rsmith rsmith   639 2007-02-18 17:57 identity.pub
-rw------- 1 rsmith rsmith  1675 2007-02-17 14:11 id_rsa
-rw------- 1 rsmith rsmith   394 2007-02-18 17:58 id_rsa.pub
-rw------- 1 rsmith rsmith  2601 2007-05-28 12:58 known_hosts
-rw------- 1 rsmith rsmith  1114 2007-05-28 12:45 rhino.pub
rsmith@atlas:~/.ssh$ diff id_dsa.pub authorized_keys2
rsmith@atlas:~/.ssh$ diff id_dsa.pub authorized_keys
rsmith@atlas:~/.ssh$ ssh rsmith@atlas
rsmith@atlas's password:

```

I can use public key authentication to log into a non-server machine but not a server.  Does the Ubuntu server configuration block public key authentication?

---

### Post by fanatik on 2007-05-30
what (if any) messages are there in /var/log/auth.log ?

---

### Post by butterman on 2007-05-31
I logged into the remote machine from the local machine and then logged into the remote machine itself, but there's nothing interesting in /var/log/auth.log.  Both sessions required my password, not the passphrase.

```
May 31 06:40:41 localhost sshd[31747]: Accepted password for rsmith from 192.168 .1.103 port 50935 ssh2
May 31 06:40:41 localhost sshd[31751]: (pam_unix) session opened for user rsmith  by (uid=0)
May 31 06:41:15 localhost sshd[31778]: Accepted password for rsmith from 127.0.0 .1 port 46501 ssh2
May 31 06:41:15 localhost sshd[31780]: (pam_unix) session opened for user rsmith  by (uid=0)
```

---

### Post by fanatik on 2007-05-31
hmm i am stumped. sorry for the lame answer, but can you try reading these 3 short articles:

[http://www.hackinglinuxexposed.com/articles/20021211.html]("http://www.hackinglinuxexposed.com/articles/20021211.html")
[http://www.hackinglinuxexposed.com/articles/20021226.html]("http://www.hackinglinuxexposed.com/articles/20021226.html")
[http://www.hackinglinuxexposed.com/articles/20030109.html]("http://www.hackinglinuxexposed.com/articles/20030109.html")

they should help!

---

