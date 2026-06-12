---
title: "ssh sftp not using public key"
date: 2017-12-22
forum: General Help
---

### Post by hansmc2 on 2017-12-22
I have a Ubuntu server that has had a ssh administration account with password access. Recently I set up a different account for a ssh folder share that can be accessed with the sftp command and a password. That all worked fine. But I found to auto mount it I need to have public key authentication. So I added a public key. But the issue is now I can log in to the administration account with the public key. But the folder share, which must be accessed with the sftp command still ask for a password. If anything, that is the opposite of what I want. So then I added &#8220;PasswordAuthentication no&#8221; to the /etc/ssh/sshd_config on the server and now folder share account will not log in at all. Bellow is the output from trying to connect. Thanks for your help.
 ```


 
  [FONT=monospace][user@computer]:~$ sftp -o "Port [port#]" -v [username@server]
OpenSSH_7.2p2 Ubuntu-4ubuntu2.2, OpenSSL 1.0.2g 1 Mar 2016 
debug1: Reading configuration data /etc/ssh/ssh_config 
debug1: /etc/ssh/ssh_config line 19: Applying options for * 
debug1: Connecting to [server] [[server]] port [port#]. 
debug1: Connection established. 
debug1: identity file /home/[username]/.ssh/id_rsa type 1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_rsa-cert type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_dsa type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_dsa-cert type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_ecdsa type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_ecdsa-cert type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_ed25519 type -1 
debug1: key_load_public: No such file or directory 
debug1: identity file /home/[username]/.ssh/id_ed25519-cert type -1 
debug1: Enabling compatibility mode for protocol 2.0 
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000 
debug1: Authenticating to [server]:[port#] as '[serveruser]' 
debug1: SSH2_MSG_KEXINIT sent 
debug1: SSH2_MSG_KEXINIT received 
debug1: kex: algorithm: curve25519-sha256@libssh.org 
debug1: kex: host key algorithm: ecdsa-sha2-nistp256 
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: no
ne 
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: no
ne 
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY 
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:[/FONT][FONT=monospace][xxx][/FONT][FONT=monospace]
debug1: Host '[[server]]:[port#]' is known and matches the ECDSA host key. 
debug1: Found key in /home/[username]/.ssh/known_hosts:1 
debug1: rekey after 134217728 blocks 
debug1: SSH2_MSG_NEWKEYS sent 
debug1: expecting SSH2_MSG_NEWKEYS 
debug1: rekey after 134217728 blocks 
debug1: SSH2_MSG_NEWKEYS received 
debug1: SSH2_MSG_EXT_INFO received 
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512> 
debug1: SSH2_MSG_SERVICE_ACCEPT received 
debug1: Authentications that can continue: publickey 
debug1: Next authentication method: publickey 
debug1: Offering RSA public key: /home/[username]/.ssh/id_rsa 
debug1: Authentications that can continue: publickey 
debug1: Trying private key: /home/[username]/.ssh/id_dsa 
debug1: Trying private key: /home/[username]/.ssh/id_ecdsa 
debug1: Trying private key: /home/[username]/.ssh/id_ed25519 
debug1: No more authentication methods to try. 
Permission denied (publickey). 
Couldn't read packet: Connection reset by peer 
[user@computer]:~$ 

[/FONT]

 

```

---

### Post by The Cog on 2017-12-22
That sounds as though authorized_keys is in the wrong location on the server. I suggest you try these commands to start with (on the server):
```
sudo -i
mkdir /home/sftp_user/.ssh
cp /home/admin_user/.ssh/authorized_keys /home/sftp_user/.ssh
chown -R sftp_user:sftp_user /home/sftp_user/.ssh
chmod 700 /home/sftp_user/.ssh
chmod 600 /home/sftp_user/.ssh/*
exit

```
This should leave you able to ssh to the server as either admin_user or sftp_user.

---

### Post by hansmc2 on 2017-12-22
Thanks for your help. That was the problem, but since this user does not have a home folder or access to any folder other then the share I had to put the key in there and add that path to the "AuthorizedKeysFile" in the "sshd_config".

---

### Post by The Cog on 2017-12-23
Good news. Thanks for the feedback.

---

