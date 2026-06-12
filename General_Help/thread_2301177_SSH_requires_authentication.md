---
title: "SSH requires authentication"
date: 2015-10-31
forum: General Help
---

### Post by ylafont on 2015-10-31
SSH requires password after keys have been installed.

I installed Ubuntu mini 14.04, and for whatever the reason I am not able to connect to it without a password via SSH.

At first I believed it was an issue with the guest machine which  generated  and copied the keys, however that is not the case.  Here is what I have done.
Machine A (Let’s call it Client), Machine B (Ubuntu Mini, let’s call it Server). Somehow what to do on which machine gets a little confusing on many of the instructions I have found.

1.       Delete all  entries  in /home/user/.ssh on both the Client and the Server  (making sure it was all clean)
[B]
On Client[/B]

1.       Generated keys **ssh-keygen **on the client**, **went through the questions and did not apply a password.
2.       Copied keys to server **ssh-copy-id [EMAIL="username@192.168.1.2"]username@192.168.1.2[/EMAIL] ** - entered password.
3.       SSH’d into server, client machine prompt for password, I check the make sure the key had been copied over the server. It was listed in the servers /home/users/.ssh/authorized_keys file

4.       I checked permission on  /home/user/.ssh folder and made sure it was 700
 
SSH always requires a password.
 
I repeated the same process on the server and was able to auto login via ssh to the client.

What setting are needed in order the properly make this work?  Thank you for the assistance.

---

### Post by Lars Noodén on 2015-10-31
You still need to point the client at the right key.  That can be done two ways.  One is to specify it when you try to connect:

```

ssh *-i /home/username/.ssh/somekey_rsa* username@192.168.1.2

```

Another is to load the key into the agent before trying to connect:

```

ssh-add */home/username/.ssh/somekey_rsa *

```

That only needs to be done once per desktop session.  It has the advantage that you can still have a strong passphrase on your key, highly recommended, yet connect without being constantly queried for it.  It has the disadvantage of working for less than 7 keys at a time.

---

### Post by ylafont on 2015-10-31
Not sure why that would need to be performed if the keys are stored in the authorized_keys file of the user one is login in as. Additionally,  i do not have to performed those steps when auto login from server to client. But i am willing to try anything.  

Received and No file or directory error. 

pi@PiScanner ~ $ ssh -i /home/username/.ssh/authorized_keys username@192.168.101.2
Warning: Identity file /home/username/.ssh/authorized_keys not accessible: No such file or directory.


**.SSH Directory on Server**
username@Server:~$ ls -ld .ssh
drwx------ 2 username username 4096 Oct 27 08:24 .ssh


**.SSH Directory Contents on Server**
[EMAIL="username@Server:~/.ssh"]username@Server:~/.ssh[/EMAIL]$ ls -l
total 16
-rw------- 1 username username  789 Oct 26 21:08 authorized_keys
-rw------- 1 username username 1675 Oct 26 20:37 id_rsa
-rw-r--r-- 1 username username  400 Oct 26 20:37 id_rsa.pub
-rw-r--r-- 1 username username  222 Oct 26 20:37 known_hosts

**Authorized Keys on Server**
[EMAIL="username@Server:~/.ssh"]username@Server:~/.ssh[/EMAIL]$ cat authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDJKqmBuPPxzFx/opVJhNQNiUUHLQIT4n2ScQljni489ONzUXmTC8fAhGprDFUhVsGZrlFm+RJrmu5VlasG+dLG33Y7mXTnhsj5FVjUzbbliUbVqizRdi18Gh6AM5VyiSqSh/prDmT5xpasQLQopGmB3kxCP6+6RnKnovUk8f4UOs4i0HXZM9VMEnwgPkN9v6LTTI7VI2QApLl/c1aYfMF2jOua/T7Xw4hdz+DbzEQi8ygk9NYpbE1QB8l4TB2Ls6hwBEVlSeHcP3H6RX8a71ow+qGz5Zz9cK5Eg6v3OKK6YXcwS2osePWgMmJsNW/mVgne3pQvoajIZyMx9+r9mCIF pi@PiScanner


**RSA Public keys on Client**
pi@PiScanner ~/.ssh $ cat id_rsa.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDJKqmBuPPxzFx/opVJhNQNiUUHLQIT4n2ScQljni489ONzUXmTC8fAhGprDFUhVsGZrlFm+RJrmu5VlasG+dLG33Y7mXTnhsj5FVjUzbbliUbVqizRdi18Gh6AM5VyiSqSh/prDmT5xpasQLQopGmB3kxCP6+6RnKnovUk8f4UOs4i0HXZM9VMEnwgPkN9v6LTTI7VI2QApLl/c1aYfMF2jOua/T7Xw4hdz+DbzEQi8ygk9NYpbE1QB8l4TB2Ls6hwBEVlSeHcP3H6RX8a71ow+qGz5Zz9cK5Eg6v3OKK6YXcwS2osePWgMmJsNW/mVgne3pQvoajIZyMx9+r9mCIF pi@PiScanner

---

### Post by Lars Noodén on 2015-10-31
On the client, the authorized keys file is not relevant.  Only the private key file is.  Try this from the client:

```
ssh -i /home/username/.ssh/**id_rsa** username@192.168.101.2

```

The client has to know which key to use.

---

### Post by ylafont on 2015-10-31
Same result.

tried the Public key (id_rsa.pub) and private (id_rsa) key files.

---

### Post by Lars Noodén on 2015-10-31
> **ylafont said:**
> Same result.

tried the ... private (id_rsa) key files.

Does the private key exist on the client in the .ssh directory?

---

### Post by ylafont on 2015-10-31
Yeap.

**.SSH Directory of Client**
pi@PiScanner ~/.ssh $ ls -l
total 12
-rw------- 1 pi pi 1675 Oct 31 11:33 id_rsa
-rw-r--r-- 1 pi pi  394 Oct 31 11:33 id_rsa.pub
-rw-r--r-- 1 pi pi  175 Oct 31 11:33 known_hosts

---

### Post by Lars Noodén on 2015-10-31
Maybe the client can give some information in a more verbose mode.

```

ssh -vv -i /home/username/.ssh/id_rsa username@192.168.101.2

```

That might give an indication as to where it is going wrong.

---

### Post by ylafont on 2015-10-31
Maybe this helps



pi@PiScanner ~/.ssh $ ssh -v username@192.168.101.2
OpenSSH_6.0p1 Debian-4+deb7u2, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.101.2 [192.168.101.2] port 22.
debug1: Connection established.
debug1: identity file /home/pi/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/pi/.ssh/id_rsa-cert type -1
debug1: identity file /home/pi/.ssh/id_dsa type -1
debug1: identity file /home/pi/.ssh/id_dsa-cert type -1
debug1: identity file /home/pi/.ssh/id_ecdsa type -1
debug1: identity file /home/pi/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4+deb7u2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 73:78:68:3b:58:0d:78:a9:64:96:6e:9c:ca:0c:ae:9f
debug1:** Host '192.168.101.2' is known and matches the ECDSA host key.**
debug1:** Found key in /home/pi/.ssh/known_hosts:1**
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: **Roaming not allowed by server**
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/pi/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/pi/.ssh/id_dsa
debug1: Trying private key: /home/pi/.ssh/id_ecdsa
debug1: Next authentication method: password
username@192.168.101.2's password

looks like keys are found.  Can the "**Roaming not allowed by server"** be it?

---

### Post by Lars Noodén on 2015-10-31
> **ylafont said:**
> 
debug1: Server host key: ECDSA 73:78:68:3b:58:0d:78:a9:64:96:6e:9c:ca:0c:ae:9f
debug1:** Host '192.168.101.2' is known and matches the ECDSA host key.**
debug1:** Found key in /home/pi/.ssh/known_hosts:1**
debug1: ssh_ecdsa_verify: signature correct

That's the client recognizing the server's key, so that it verifies that it is connecting to the right host.  

> **ylafont said:**
> 
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/pi/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password

It doesn't seem to like that key.  Which options did you use with ssh-keygen?

---

### Post by ylafont on 2015-10-31
no option,  just [B]ssh-keygen

[/B]Just re did everything with and got the same result.

ssh-keygen -t rsa

---

### Post by Lars Noodén on 2015-10-31
Strange.  What about the server's configuration?

```

/usr/sbin/sshd -T | sort

```

---

### Post by ylafont on 2015-10-31
Well at lest you have confirm my suspicion that i am  not going crazy!  thank you for all the assistance.


**Server Config**
USername@Server:~$ /usr/sbin/sshd -T | sort
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key
Could not load host key: /etc/ssh/ssh_host_ed25519_key
acceptenv LANG
acceptenv LC_*
addressfamily any
allowtcpforwarding yes
authenticationmethods
authorizedkeysfile .ssh/authorized_keys .ssh/authorized_keys2 
challengeresponseauthentication no
ciphers 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,arcfour128,arcfour256,aes128-cbc,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com
clientalivecountmax 3
clientaliveinterval 0
compression delayed
gatewayports no
gssapiauthentication no
gssapicleanupcredentials yes
gssapikeyexchange no
gssapistorecredentialsonrekey no
gssapistrictacceptorcheck yes
hostbasedauthentication no
hostbasedusesnamefrompacketonly no
hostkey /etc/ssh/ssh_host_dsa_key
hostkey /etc/ssh/ssh_host_ecdsa_key
hostkey /etc/ssh/ssh_host_ed25519_key
hostkey /etc/ssh/ssh_host_rsa_key
ignorerhosts yes
ignoreuserknownhosts no
ipqos lowdelay throughput
kbdinteractiveauthentication no
kerberosauthentication no
kerberosorlocalpasswd yes
kerberosticketcleanup yes
kexalgorithms diffie-hellman-group1-sha1,diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diffie-hellman-group-exchange-sha256,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group1-sha1,curve25519-sha256@libssh.org
keyregenerationinterval 3600
listenaddress 0.0.0.0:22
listenaddress [::]:22
logingracetime 120
loglevel INFO
macs hmac-sha1,hmac-sha1-96,hmac-sha2-256,hmac-sha2-512,hmac-md5,hmac-md5-96,hmac-ripemd160,hmac-ripemd160@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha1-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-md5-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-ripemd160-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com
maxauthtries 6
maxsessions 10
maxstartups 10:30:100
passwordauthentication yes
permitemptypasswords no
permitopen any
permitrootlogin without-password
permittty yes
permittunnel no
permituserenvironment no
pidfile /var/run/sshd.pid
port 22
printlastlog yes
printmotd no
protocol 2
pubkeyauthentication yes
rekeylimit 0 0
rhostsrsaauthentication no
rsaauthentication yes
serverkeybits 1024
strictmodes yes
subsystem sftp /usr/lib/openssh/sftp-server
syslogfacility AUTH
tcpkeepalive yes
usedns yes
uselogin no
usepam 1
useprivilegeseparation yes
versionaddendum
x11displayoffset 10
x11forwarding yes
x11uselocalhost yes
xauthlocation /usr/bin/xauth

---

### Post by Lars Noodén on 2015-10-31
No worries.  But I'm quite puzzled.  The parts that I know to look at seem ok:

> **ylafont said:**
> 
...
authorizedkeysfile .ssh/authorized_keys .ssh/authorized_keys2 
...
pubkeyauthentication yes
...

What about the client at full verbosity?  -vvv

---

### Post by ylafont on 2015-10-31
[B]

pi@PiScanner ~/.ssh $ ssh -vvv username@192.168.101.2[/B]
OpenSSH_6.0p1 Debian-4+deb7u2, OpenSSL 1.0.1e 11 Feb 2013
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.101.2 [192.168.101.2] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/pi/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/pi/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/pi/.ssh/id_rsa-cert type -1
debug1: identity file /home/pi/.ssh/id_dsa type -1
debug1: identity file /home/pi/.ssh/id_dsa-cert type -1
debug1: identity file /home/pi/.ssh/id_ecdsa type -1
debug1: identity file /home/pi/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2.3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.0p1 Debian-4+deb7u2
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "192.168.101.2" from file "/home/pi/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/pi/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com[/email],ecdsa-sha2-nistp52                                                       [email]1-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-excha                                                       nge-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com[/email],ecdsa-sha2-nistp521-cert-v01@openssh.c                                                       om,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-rsa-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.c                                                       om,ssh-dss-cert-v00@openssh.com,ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cb                                                       c,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cb                                                       c,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac                                                       [email]-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-sha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac                                                       [email]-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: [email]curve25519-sha256@libssh.org[/email],ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha2                                                       56,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss,ecdsa-sha2-nistp256,ssh-ed25519
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@o                                                       penssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@o                                                       penssh.com,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-etm@op                                                       enssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,                                                       [email]umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: [email]hmac-md5-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64-etm@openssh.com,umac-128-etm@openssh.com[/email],hmac-sha2-256-etm@op                                                       enssh.com,hmac-sha2-512-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-sha1,                                                       [email]umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-ripemd160,hmac-ripemd160@openssh.com[/email],hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 73:78:68:3b:58:0d:78:a9:64:96:6e:9c:ca:0c:ae:9f
debug3: load_hostkeys: loading entries for host "192.168.101.2" from file "/home/pi/.ssh/known_hosts"
debug3: load_hostkeys: found key type ECDSA in file /home/pi/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '192.168.101.2' is known and matches the ECDSA host key.
debug1: Found key in /home/pi/.ssh/known_hosts:1
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
debug2: key: /home/pi/.ssh/id_rsa (0x782a3308)
debug2: key: /home/pi/.ssh/id_dsa ((nil))
debug2: key: /home/pi/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/pi/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/pi/.ssh/id_dsa
debug3: no such identity: /home/pi/.ssh/id_dsa
debug1: Trying private key: /home/pi/.ssh/id_ecdsa
debug3: no such identity: /home/pi/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
username@192.168.101.2's password:

---

### Post by HermanAB on 2015-10-31
Well, it looks to me that it is telling you what is the matter:
debug1: Trying private key: /home/pi/.ssh/id_dsa
debug3: no such identity: /home/pi/.ssh/id_dsa
debug1: Trying private key: /home/pi/.ssh/id_ecdsa
debug3: no such identity: /home/pi/.ssh/id_ecdsa

---

### Post by Lars Noodén on 2015-10-31
This part looks suspicious to me:

> **ylafont said:**
> 
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/pi/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/pi/.ssh/id_rsa type 1

Between that and generating the key pair without options, I would suggest generating a new key pair and adding that to authorized_keys on the server.

```

ssh-keygen -b 2048 -t rsa -C "key for .1.2" -f /home/pi/.ssh/key_rsa

```

---

### Post by ylafont on 2015-10-31
Those seem to be for other authentication metods. if i were to get one that states 

[B][COLOR=#000000]debug1: Trying private key: /home/pi/.ssh/id_rsa[/COLOR]
[/B][COLOR=#000000][B]debug3: no such identity: /home/pi/.ssh/id_rsa
[/B]
then i would worry. 


In continuing to explore, i get this in /var/log/auth.log

[/COLOR]**Oct 31 14:00:20 EclipseOne sshd[3172]: Authentication refused: bad ownership or modes for directory /home/username**

Which i cant figure out.

---

### Post by Lars Noodén on 2015-10-31
> **ylafont said:**
> **Oct 31 14:00:20 EclipseOne sshd[3172]: Authentication refused: bad ownership or modes for directory /home/username**


That might be it.  What are the permissions for /home/ and /home/username/ ?  They should be something where Other cannot write.

---

### Post by ylafont on 2015-10-31
Damn..   In all my checking, i was only paying attention to the ~/.ssh directory on the server.  those were correct.  /home/username also needed to be adjusted.  I just set them to 744 and went right in!

Thank you for all the assistance Lars!

---

