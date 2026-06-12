---
title: "server's ssh cert regen after cloning"
date: 2022-12-08
forum: General Help
---

### Post by ant2ne on 2022-12-08
New clone. Ssh from client to this clone causees a known hosts error. I need to regen the server ssh cert (not the user's /home/user/.ssh/???) after cloning. I know what I need to do but I don't know how to describe it or choose the correct keywords in a google search. I would be appreciative if someone could give me a hint as to how I gen new server ssh certs.

Moderators: If this is posted in the wrong forum, please move.

---

### Post by TheFu on 2022-12-08
If it were me, I'd just use 
```
sudo apt purge ssh
sudo apt install ssh
```

That should force the installer to create new server certs, but I haven't tested it.  During the install, the ssh-cert creation is fairly obvious in the output.

Congratulations on your clone.  Is it a boy or girl? Which animal?

---

### Post by MAFoElffen on 2022-12-08
The wording is: How to fix "host key verification failed ssh error"...

Error will be something like: "Offending RSA key in /ua/username/.ssh/known_hosts:5"

Which means remove line #5 of file $HOME/.ssh/known_hosts...

Then on client
```
ssh-keygen
ssh-copy-id -i [ssh-key-location] [username]@[server-ip-address]

```

---

### Post by TheFu on 2022-12-08
> **ant2ne said:**
> New clone. Ssh from client to this clone causees a known hosts error. I need to regen the server ssh cert (not the user's /home/user/.ssh/???) after cloning. I know what I need to do but I don't know how to describe it or choose the correct keywords in a google search. I would be appreciative if someone could give me a hint as to how I gen new server ssh certs.

Moderators: If this is posted in the wrong forum, please move.

Actually, if you'd do the ssh attempt and copy/paste the exact results, we'd likely know exactly what the issue is.  The messages from failed ssh connections are clear.  And if it is something else, ssh supports requesting more verbosity, so it becomes clear what the root cause is without any guessing needed.

---

### Post by ant2ne on 2022-12-09
```
ssh -vvv 192.168.1.113
OpenSSH_8.9p1 Ubuntu-3, OpenSSL 3.0.2 15 Mar 2022
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.1.113 is address
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/home/ant2ne/.ssh/known_hosts'
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/home/ant2ne/.ssh/known_hosts2'
debug3: ssh_connect_direct: entering
debug1: Connecting to 192.168.1.113 [192.168.1.113] port 22.
debug3: set_sock_tos: set socket 3 IP_TOS 0x10
debug1: Connection established.
debug1: identity file /home/ant2ne/.ssh/id_rsa type 0
debug1: identity file /home/ant2ne/.ssh/id_rsa-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_ecdsa type -1
debug1: identity file /home/ant2ne/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_ecdsa_sk type -1
debug1: identity file /home/ant2ne/.ssh/id_ecdsa_sk-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_ed25519 type -1
debug1: identity file /home/ant2ne/.ssh/id_ed25519-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_ed25519_sk type -1
debug1: identity file /home/ant2ne/.ssh/id_ed25519_sk-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_xmss type -1
debug1: identity file /home/ant2ne/.ssh/id_xmss-cert type -1
debug1: identity file /home/ant2ne/.ssh/id_dsa type -1
debug1: identity file /home/ant2ne/.ssh/id_dsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.9p1 Ubuntu-3
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.9p1 Ubuntu-3
debug1: compat_banner: match: OpenSSH_8.9p1 Ubuntu-3 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.1.113:22 as 'ant2ne'
debug1: load_hostkeys: fopen /home/ant2ne/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug3: order_hostkeyalgs: no algorithms matched; accept original
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,ext-info-c
debug2: host key algorithms: ssh-ed25519-cert-v01@openssh.com,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,sk-ssh-ed25519-cert-v01@openssh.com,sk-ecdsa-sha2-nistp256-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-ed25519,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ssh-ed25519@openssh.com,sk-ecdsa-sha2-nistp256@openssh.com,rsa-sha2-512,rsa-sha2-256
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,sntrup761x25519-sha512@openssh.com,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256
debug2: host key algorithms: rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
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
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ssh-ed25519
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-ed25519 SHA256:6hU1cPv2NavvWxobDVFqo6fX3uDQn9h6kfH/nbvV7QE
debug1: load_hostkeys: fopen /home/ant2ne/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug3: hostkeys_find_by_key_hostfile: trying user hostfile "/home/ant2ne/.ssh/known_hosts"
debug3: hostkeys_foreach: reading file "/home/ant2ne/.ssh/known_hosts"
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:37
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:40
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:45
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:46
debug1: hostkeys_find_by_key_cb: found matching key in ~/.ssh/known_hosts:47
debug3: hostkeys_find_by_key_hostfile: trying user hostfile "/home/ant2ne/.ssh/known_hosts2"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /home/ant2ne/.ssh/known_hosts2 does not exist
debug3: hostkeys_find_by_key_hostfile: trying system hostfile "/etc/ssh/ssh_known_hosts"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts does not exist
debug3: hostkeys_find_by_key_hostfile: trying system hostfile "/etc/ssh/ssh_known_hosts2"
debug1: hostkeys_find_by_key_hostfile: hostkeys file /etc/ssh/ssh_known_hosts2 does not exist
The authenticity of host '192.168.1.113 (192.168.1.113)' can't be established.
ED25519 key fingerprint is SHA256:6hU1cPv2NavvWxobDVFqo6fX3uDQn9h6kfH/nbvV7QE.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:37: [hashed name]
    ~/.ssh/known_hosts:40: [hashed name]
    ~/.ssh/known_hosts:45: [hashed name]
    ~/.ssh/known_hosts:46: [hashed name]
    ~/.ssh/known_hosts:47: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? 

```I assume 37 40 45 46 47 are all clones. I spin them up, for testing, then trash them. Or, some I keep for other purposes.

---

### Post by SeijiSensei on 2022-12-09
I'd start with a new $USER/.ssh directory, then run ssh-genkey to create a new key for yourself.

And, like TheFu, I'd remove and reinstall ssh on the server.

---

### Post by ant2ne on 2022-12-09
I do plan to redo my user login ssh keys. But that isn't the keys I am talking about. as MAFoElffen said, I need to renew the host key, not the user key. I don't think renewal of user key will renew the host key.

---

### Post by TheFu on 2022-12-09
I'd always remove the ~/.ssh/known_hosts after every new cloned server was put up.  Conflicts aren't good and there could be strict validation settings on the server or the client to prevent connections.

Considering that I can't remember the last time I had to regenerate host keys for /etc/ssh/, I'm not too confident that will help.  In recent releases, some older ciphers were deprecated and there are rumors that elliptical keys have been cracked by the NSA using a quantum computer. Those are just rumors, of course.  The people who think that's true are using 8k RSA keys now.

I suppose the good news is that nothing trivial is jumping out, which I didn't expect.

---

### Post by MAFoElffen on 2022-12-09
As TheFu said, and as we both do, we both do VM hosting and clone machines. We both use KVM. As it sound like you are cloning guests. Let me be a bit more specific in how I describe the host and client.

If after a clone process, the target server system that you connect to, I will refer to as the target or host system. The connecting system, the source, I will refer to as the client...

The host system sits there with a listening port open waitng for a client to call it... It has the known_host file on it located in a directory in the logged in User's Home directory... I will refer to the User's Home directory as the variable $HOME. The known_hosts file is located at $HOME/.ssh/known_hosts. That file stores information from what has connected to it.

Since the instance is a clone of another machine, it is a duplicate from the old machine. When you first install openssh-server, that whole directory does not exist. It is created the first time someone connects via a client to a user on the host machine, and is created in that User's Home folder. So deleting that folder will let you start fresh.

So on the host:
```

rm -R $HOME/.ssh/*    ## Will delete everything in that directory
rmdir $HOME/.ssh       ## Will remove that directory

```
If a host exists a while and you change the IP address of the client, then you will also get a known_host error, saying that host exists with conflicting connection data... Then you might not want to start all over again, and would just remove the connection data fro the specific line of that file. Then you would edit the file to remove that one offending line... Either way will work for that error... But since it is a clone... It may be easier to start fresh.

On clients, use the copy id command to copy over old keys to the new host.

if the clone is the client, then you would need to regen a new ssh key.

Does that clear up confusions from a previously summarized answer?

---

