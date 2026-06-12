---
title: "SSH: Host key verification failed. No known hosts file"
date: 2017-11-12
forum: General Help
---

### Post by smoestar on 2017-11-12
[COLOR=#000000][FONT=proxima-nova]Hello! I'm fairly new to all of this, and i have recently rented a droplet. I'm trying to connect to the droplet via SSH on my ubuntu, but i keep getting error messages - and i've googled my ass of without getting any smarter.[/FONT][/COLOR]
[COLOR=#000000][FONT=proxima-nova]sidenote before i post the errormessags: It worked perfectly fine on my desktop(win 10, putty)
I've deleted the droplet and createt several new keys and tried over and over again. On my current droplet i have not been able to connect at all via ssh. I have not tried windows.
I do not have a known hosts file.


Please dear linux gods. Show me the way.[/FONT][/COLOR]
[COLOR=#000000][FONT=proxima-nova]ssh -vv root@ip gives me:[/FONT][/COLOR]
```
OpenSSH_7.5p1 Ubuntu-10, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "198.211.123.63" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 198.211.123.63 [198.211.123.63] port 22.
debug1: Connection established.
debug1: identity file /home/sverre/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/sverre/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.5p1 Ubuntu-10
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 198.211.123.63:22 as 'root'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,aes128-cbc,aes192-cbc,aes256-cbc
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256@libssh.org
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:Rw7hDMScFl+1Og3XLsxE5MlXV/ctjv7WSvKy6y/mTuY
The authenticity of host '198.211.123.63 (198.211.123.63)' can't be established.
ECDSA key fingerprint is SHA256:Rw7hDMScFl+1Og3XLsxE5MlXV/ctjv7WSvKy6y/mTuY.
Are you sure you want to continue connecting (yes/no)? 
Host key verification failed.
```

---

### Post by TheFu on 2017-11-12
On the server - **sudo apt install openssh-server fail2ban**  # I always install fail2ban on every ssh-server to automatically firewall failed attempts quickly (on port 22/tcp)

On the client - **sudo apt install ssh**
On the client - **ssh-keygen {plus whatever options you like}** #  be certain to set a passphrase
On the client - **ssh-copy-id userid-yours@IP-of-the-server**   # you should be prompted for the ssh-key passphrase followed by the userid-yours password on the server.
On the client, **ssh userid-yours@IP-of-the-server**

Be happy.

The installations and key-gen stuff only need happen once per client.  ssh-copy-id ensures the files and directories involved have the correct permissions. ssh is picky about those things and it is easy to screw up.

Use the ~/.ssh/config file to setup aliases for connections to different servers. Never have to know the userid or port or IP/server-name for the remote system.  Call it something that makes sense to you - "bob", if you like. ;)  man ssh_config explains the file format.  All libssh tools honor these settings, so x2go, rsync, rdiff-backup, scp, sftp, ssh, and 50 other tools use those settings too.

If this isn't enough, I wrote up an ssh troubleshooting article: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

Not all servers support all the ciphers that every client supports.

---

