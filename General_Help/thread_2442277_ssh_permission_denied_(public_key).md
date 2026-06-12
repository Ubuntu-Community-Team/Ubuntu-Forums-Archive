---
title: "ssh permission denied (public key)"
date: 2020-05-01
forum: General Help
---

### Post by kjaspan on 2020-05-01
I have read DOZENS of the postings I found by searching with the string in the subject above and none helps.

I am missing something - probably elementary - and need another/many pair of eyes to see what that is.

So here's what I did. I upgraded my development desktop from Ubuntu 19.10 to 20.04 but, wisely, have not upgraded my "production" desktop from 18.04 yet and won't do so until all my applications work properly.

ssh seemed OK on the 20.04 "client" until I started to tweak it to get Mysql Workbench to connect to the server. I ran the command:

snap connect mysql-workbench-community:ssh-keys

and, maybe coincidentally, ssh to the server failed with the above error.

Here is the output of the command ssh -i -vvv server_ip

`OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n 7 Dec 2017 debug1: Reading configuration data /etc/ssh/ssh_config debug1: /etc/ssh/ssh_config line 19: Applying options for * debug2: resolving "192.168.1.10" port 22 debug2: ssh_connect_direct: needpriv 0 debug1: Connecting to 192.168.1.10 [192.168.1.10] port 22. debug1: Connection established. debug1: permanently_set_uid: 0/0 debug1: identity file /root/.ssh/id_rsa.pub type 0 debug1: key_load_public: No such file or directory debug1: identity file /root/.ssh/id_rsa.pub-cert type -1 debug1: identity file /root/.ssh/id_rsa type 0 debug1: key_load_public: No such file or directory debug1: identity file /root/.ssh/id_rsa-cert type -1 debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000 debug2: fd 3 setting O_NONBLOCK debug1: Authenticating to 192.168.1.10:22 as 'root' debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts" debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:2 debug3: load_hostkeys: loaded 1 keys from 192.168.1.10 debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521 debug3: send packet: type 20 debug1: SSH2_MSG_KEXINIT sent debug3: receive packet: type 20 debug1: SSH2_MSG_KEXINIT received debug2: local client KEXINIT proposal debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c debug2: host key algorithms: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com[/email],ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: compression ctos: none,zlib@openssh.com,zlib debug2: compression stoc: none,zlib@openssh.com,zlib debug2: languages ctos: debug2: languages stoc: debug2: first_kex_follows 0 debug2: reserved 0 debug2: peer server KEXINIT proposal debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1 debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519 debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: compression ctos: none,zlib@openssh.com debug2: compression stoc: none,zlib@openssh.com debug2: languages ctos: debug2: languages stoc: debug2: first_kex_follows 0 debug2: reserved 0 debug1: kex: algorithm: curve25519-sha256 debug1: kex: host key algorithm: ecdsa-sha2-nistp256 debug1: kex: server->client cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: compression: none debug1: kex: client->server cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: compression: none debug3: send packet: type 30 debug1: expecting SSH2_MSG_KEX_ECDH_REPLY debug3: receive packet: type 31 debug1: Server host key: ecdsa-sha2-nistp256 SHA256:ihT4T/0uZlh6ujuMQIWNoKWdf8zONBap92BeMbstNtg debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts" debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:2 debug3: load_hostkeys: loaded 1 keys from 192.168.1.10 debug1: Host '192.168.1.10' is known and matches the ECDSA host key. debug1: Found key in /root/.ssh/known_hosts:2 debug3: send packet: type 21 debug2: set_newkeys: mode 1 debug1: rekey after 134217728 blocks debug1: SSH2_MSG_NEWKEYS sent debug1: expecting SSH2_MSG_NEWKEYS debug3: receive packet: type 21 debug1: SSH2_MSG_NEWKEYS received debug2: set_newkeys: mode 0 debug1: rekey after 134217728 blocks debug2: key: /root/.ssh/id_rsa.pub (0x55ee3b0d8ad0), explicit debug2: key: /root/.ssh/id_rsa (0x55ee3b0d7d30) debug3: send packet: type 5 debug3: receive packet: type 7 debug1: SSH2_MSG_EXT_INFO received debug1: kex_input_ext_info: server-sig-algs= debug3: receive packet: type 6 debug2: service_accept: ssh-userauth debug1: SSH2_MSG_SERVICE_ACCEPT received debug3: send packet: type 50 debug3: receive packet: type 53 debug3: input_userauth_banner Ubuntu 18.04.4 LTS \n \l

debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug3: start over, passed a different list publickey debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive debug3: authmethod_lookup publickey debug3: remaining preferred: keyboard-interactive debug3: authmethod_is_enabled publickey debug1: Next authentication method: publickey debug1: Offering public key: RSA SHA256:sOPLHvZ4E2sxXV2Cvs2/HqGH5Rkx/Wx2KdSsNULofl8 /root/.ssh/id_rsa.pub debug3: send_pubkey_test debug3: send packet: type 50 debug2: we sent a publickey packet, wait for reply debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug1: Offering public key: RSA SHA256:sOPLHvZ4E2sxXV2Cvs2/HqGH5Rkx/Wx2KdSsNULofl8 /root/.ssh/id_rsa debug3: send_pubkey_test debug3: send packet: type 50 debug2: we sent a publickey packet, wait for reply debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug2: we did not send a packet, disable method debug1: No more authentication methods to try. root@192.168.1.10: Permission denied (publickey).`


Where is it getting the public key SHA256:sOPLHvZ4E... from? I can find no such string in any of the id_rsa* files, nor the authorized_keys on the server.

Here's what I have done: 
1. apt-get remove ssh 

2. apt-get purge ssh both on client, then reinstalled 

3. apt-get install openssh-client

On the server 
apt-get remove ssh

apt-get remove openssh-server 

apt-get purge ssh 

apt-get purge openssh-server

My permissions on both server and client are 700 for /root/.ssh directories, 644 for id_rsa.pub and 600 for id_rsa

I ran ssh-keygen on client and copied the contents of id_rsa.pub to authorized_keys on the server. 

In /etc/ssh/ssh_config on both machines I have 

PasswordAuthentication no

IdentityFile ~/.ssh/id_rsa On the client in /etc/ssh/sshd_config I have PubkeyAuthentication yes

RSAAuthentication    yes

PasswordAuthentication no 

but I also have the following lines commented out (is this OK?) 

`#AuthorizedKeysFile .ssh/authorized_keys .ssh/authorized_keys2

AuthorizedPrincipalsFile none

AuthorizedKeysCommand none

AuthorizedKeysCommandUser nobody`

and 

X11Forwarding no

MaxStartups 2:30:10

AllowUsers  <me> root

On the server: In ssh_config: 

PasswordAuthentication no
   IdentityFile ~/.ssh/id_rsa ------> should this be authorized_keys??? 

In sshd_config: 
`LogLevel VERBOSE 

LoginGraceTime 30 

PermitRootLogin yes 

RSAAuthentication yes

AuthorizedKeysFile .ssh/authorized_keys .ssh/authorized_keys2

PasswordAuthentication no 

AllowTcpForwarding no 

MaxStartups 2:30:10`

The /var/log/auth.log has nothing spectacular in it, that catches my eye.

I ran eval $(ssh-agent) on both boxes and both showed a pid. I ran ssh-add with no parameters on the server. That didn't fix the problem.

Restarted ssh-agent. eval now shows different pids on the 2 machines. ssh failed again with same error. 

So, can any of your eyes catch the cause of the error?

Thanks in advance.

---

### Post by kjaspan on 2020-05-05
> **kjaspan said:**
> I have read DOZENS of the postings I found by searching with the string in the subject above and none helps.

I am missing something - probably elementary - and need another/many pair of eyes to see what that is.

So here's what I did. I upgraded my development desktop from Ubuntu 19.10 to 20.04 but, wisely, have not upgraded my "production" desktop from 18.04 yet and won't do so until all my applications work properly.

ssh seemed OK on the 20.04 "client" until I started to tweak it to get Mysql Workbench to connect to the server. I ran the command:

snap connect mysql-workbench-community:ssh-keys

and, maybe coincidentally, ssh to the server failed with the above error.

Here is the output of the command ssh -i -vvv server_ip

`OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n 7 Dec 2017 debug1: Reading configuration data /etc/ssh/ssh_config debug1: /etc/ssh/ssh_config line 19: Applying options for * debug2: resolving "192.168.1.10" port 22 debug2: ssh_connect_direct: needpriv 0 debug1: Connecting to 192.168.1.10 [192.168.1.10] port 22. debug1: Connection established. debug1: permanently_set_uid: 0/0 debug1: identity file /root/.ssh/id_rsa.pub type 0 debug1: key_load_public: No such file or directory debug1: identity file /root/.ssh/id_rsa.pub-cert type -1 debug1: identity file /root/.ssh/id_rsa type 0 debug1: key_load_public: No such file or directory debug1: identity file /root/.ssh/id_rsa-cert type -1 debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH* compat 0x04000000 debug2: fd 3 setting O_NONBLOCK debug1: Authenticating to 192.168.1.10:22 as 'root' debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts" debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:2 debug3: load_hostkeys: loaded 1 keys from 192.168.1.10 debug3: order_hostkeyalgs: prefer hostkeyalgs: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com[/email],ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521 debug3: send packet: type 20 debug1: SSH2_MSG_KEXINIT sent debug3: receive packet: type 20 debug1: SSH2_MSG_KEXINIT received debug2: local client KEXINIT proposal debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c debug2: host key algorithms: [email]ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com[/email],ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: compression ctos: none,zlib@openssh.com,zlib debug2: compression stoc: none,zlib@openssh.com,zlib debug2: languages ctos: debug2: languages stoc: debug2: first_kex_follows 0 debug2: reserved 0 debug2: peer server KEXINIT proposal debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1 debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519 debug2: ciphers ctos: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: ciphers stoc: [email]chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com[/email] debug2: MACs ctos: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: MACs stoc: [email]umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com[/email],hmac-sha2-256,hmac-sha2-512,hmac-sha1 debug2: compression ctos: none,zlib@openssh.com debug2: compression stoc: none,zlib@openssh.com debug2: languages ctos: debug2: languages stoc: debug2: first_kex_follows 0 debug2: reserved 0 debug1: kex: algorithm: curve25519-sha256 debug1: kex: host key algorithm: ecdsa-sha2-nistp256 debug1: kex: server->client cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: compression: none debug1: kex: client->server cipher: [email]chacha20-poly1305@openssh.com[/email] MAC: compression: none debug3: send packet: type 30 debug1: expecting SSH2_MSG_KEX_ECDH_REPLY debug3: receive packet: type 31 debug1: Server host key: ecdsa-sha2-nistp256 SHA256:ihT4T/0uZlh6ujuMQIWNoKWdf8zONBap92BeMbstNtg debug3: hostkeys_foreach: reading file "/root/.ssh/known_hosts" debug3: record_hostkey: found key type ECDSA in file /root/.ssh/known_hosts:2 debug3: load_hostkeys: loaded 1 keys from 192.168.1.10 debug1: Host '192.168.1.10' is known and matches the ECDSA host key. debug1: Found key in /root/.ssh/known_hosts:2 debug3: send packet: type 21 debug2: set_newkeys: mode 1 debug1: rekey after 134217728 blocks debug1: SSH2_MSG_NEWKEYS sent debug1: expecting SSH2_MSG_NEWKEYS debug3: receive packet: type 21 debug1: SSH2_MSG_NEWKEYS received debug2: set_newkeys: mode 0 debug1: rekey after 134217728 blocks debug2: key: /root/.ssh/id_rsa.pub (0x55ee3b0d8ad0), explicit debug2: key: /root/.ssh/id_rsa (0x55ee3b0d7d30) debug3: send packet: type 5 debug3: receive packet: type 7 debug1: SSH2_MSG_EXT_INFO received debug1: kex_input_ext_info: server-sig-algs= debug3: receive packet: type 6 debug2: service_accept: ssh-userauth debug1: SSH2_MSG_SERVICE_ACCEPT received debug3: send packet: type 50 debug3: receive packet: type 53 debug3: input_userauth_banner Ubuntu 18.04.4 LTS \n \l

debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug3: start over, passed a different list publickey debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive debug3: authmethod_lookup publickey debug3: remaining preferred: keyboard-interactive debug3: authmethod_is_enabled publickey debug1: Next authentication method: publickey debug1: Offering public key: RSA SHA256:sOPLHvZ4E2sxXV2Cvs2/HqGH5Rkx/Wx2KdSsNULofl8 /root/.ssh/id_rsa.pub debug3: send_pubkey_test debug3: send packet: type 50 debug2: we sent a publickey packet, wait for reply debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug1: Offering public key: RSA SHA256:sOPLHvZ4E2sxXV2Cvs2/HqGH5Rkx/Wx2KdSsNULofl8 /root/.ssh/id_rsa debug3: send_pubkey_test debug3: send packet: type 50 debug2: we sent a publickey packet, wait for reply debug3: receive packet: type 51 debug1: Authentications that can continue: publickey debug2: we did not send a packet, disable method debug1: No more authentication methods to try. root@192.168.1.10: Permission denied (publickey).`


Where is it getting the public key SHA256:sOPLHvZ4E... from? I can find no such string in any of the id_rsa* files, nor the authorized_keys on the server.

Here's what I have done: 
1. apt-get remove ssh 

2. apt-get purge ssh both on client, then reinstalled 

3. apt-get install openssh-client

On the server 
apt-get remove ssh

apt-get remove openssh-server 

apt-get purge ssh 

apt-get purge openssh-server

My permissions on both server and client are 700 for /root/.ssh directories, 644 for id_rsa.pub and 600 for id_rsa

I ran ssh-keygen on client and copied the contents of id_rsa.pub to authorized_keys on the server. 

In /etc/ssh/ssh_config on both machines I have 

PasswordAuthentication no

IdentityFile ~/.ssh/id_rsa On the client in /etc/ssh/sshd_config I have PubkeyAuthentication yes

RSAAuthentication    yes

PasswordAuthentication no 

but I also have the following lines commented out (is this OK?) 

`#AuthorizedKeysFile .ssh/authorized_keys .ssh/authorized_keys2

AuthorizedPrincipalsFile none

AuthorizedKeysCommand none

AuthorizedKeysCommandUser nobody`

and 

X11Forwarding no

MaxStartups 2:30:10

AllowUsers  <me> root

On the server: In ssh_config: 

PasswordAuthentication no
   IdentityFile ~/.ssh/id_rsa ------> should this be authorized_keys??? 

In sshd_config: 
`LogLevel VERBOSE 

LoginGraceTime 30 

PermitRootLogin yes 

RSAAuthentication yes

AuthorizedKeysFile .ssh/authorized_keys .ssh/authorized_keys2

PasswordAuthentication no 

AllowTcpForwarding no 

MaxStartups 2:30:10`

The /var/log/auth.log has nothing spectacular in it, that catches my eye.

I ran eval $(ssh-agent) on both boxes and both showed a pid. I ran ssh-add with no parameters on the server. That didn't fix the problem.

Restarted ssh-agent. eval now shows different pids on the 2 machines. ssh failed again with same error. 

So, can any of your eyes catch the cause of the error?

Thanks in advance.

I solved this problem - amazingly simple - by installing openssh-server on the local client!!!!

---

