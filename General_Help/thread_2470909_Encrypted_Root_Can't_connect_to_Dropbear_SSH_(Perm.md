---
title: "Encrypted Root: Can't connect to Dropbear SSH (Permission denied (publickey))"
date: 2022-01-16
forum: General Help
---

### Post by sandman852 on 2022-01-16
Hi all, 

[COLOR=#232629][FONT=-apple-system]I'm running my home server (Ubuntu 20.04 LTS) with encrypted root and try to use dropbear in initramfs to be able to unlock it remotely during boot. To setup the remote unlocking ability I was following basically this guide: [/FONT][/COLOR][How to install LUKS encrypted Ubuntu 18.04.x Server and enable remote unlocking]("https://hamy.io/post/0009/how-to-install-luks-encrypted-ubuntu-18.04.x-server-and-enable-remote-unlocking/#gsc.tab=0")

[COLOR=#232629][FONT=-apple-system]On my MacBook I've successfully created a pair of ssh keys:
[/FONT][/COLOR]```
[FONT=var(--ff-mono)]
(base) myuser@myMBP ~ % ssh-keygen -t rsa -b 4096[/FONT]
```

[COLOR=#232629][FONT=-apple-system]After that I have been adding the newly generated public key to /etc/dropbear-initramfs/authorized_keys:

[/FONT][/COLOR]```
myuser@myserver:~$ cat /etc/dropbear-initramfs/authorized_keys 
no-port-forwarding,no-agent-forwarding,no-x11-forwarding,command=/bin/cryptroot-unlock ssh-rsa <here-goes-my-ssh-pubkey> myuser@myMBP.local

```

After that, running ```
myuser@myserver:~$ sudo update-initramfs -c -k all
``` all went fine.

[COLOR=#232629][FONT=-apple-system]However, trying to login to the Dropbear SSH server doesn't work:
[/FONT][/COLOR]```
(base) myuser@myMBP ~ % ssh -i ~/.ssh/id_rsa -o "HostKeyAlgorithms ssh-rsa" -p 9999 root@192.168.xxx.xxx -vvv
OpenSSH_8.6p1, LibreSSL 2.8.3
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 21: include /etc/ssh/ssh_config.d/* matched no files
debug1: /etc/ssh/ssh_config line 54: Applying options for *
debug2: resolve_canonicalize: hostname 192.168.xxx.xxx is address
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts' -> '/Users/myuser/.ssh/known_hosts'
debug3: expanded UserKnownHostsFile '~/.ssh/known_hosts2' -> '/Users/myuser/.ssh/known_hosts2'
debug1: Authenticator provider $SSH_SK_PROVIDER did not resolve; disabling
debug3: ssh_connect_direct: entering
debug1: Connecting to 192.168.xxx.xxx [192.168.xxx.xxx] port 9999.
debug3: set_sock_tos: set socket 3 IP_TOS 0x48
debug1: Connection established.
debug1: identity file /Users/myuser/.ssh/id_rsa type 0
debug1: identity file /Users/myuser/.ssh/id_rsa-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_8.6
debug1: Remote protocol version 2.0, remote software version dropbear_2019.78
debug1: compat_banner: no match: dropbear_2019.78
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.xxx.xxx:9999 as 'root'
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,ext-info-c
debug2: host key algorithms: ssh-rsa
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
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp521,ecdh-sha2-nistp384,ecdh-sha2-nistp256,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,kexguess2@matt.ucc.asn.au
debug2: host key algorithms: ecdsa-sha2-nistp256,ssh-rsa,ssh-dss
debug2: ciphers ctos: aes128-ctr,aes256-ctr,aes128-cbc,aes256-cbc,3des-ctr,3des-cbc
debug2: ciphers stoc: aes128-ctr,aes256-ctr,aes128-cbc,aes256-cbc,3des-ctr,3des-cbc
debug2: MACs ctos: hmac-sha1-96,hmac-sha1,hmac-sha2-256
debug2: MACs stoc: hmac-sha1-96,hmac-sha1,hmac-sha2-256
debug2: compression ctos: zlib@openssh.com,none
debug2: compression stoc: zlib@openssh.com,none
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ssh-rsa
debug1: kex: server->client cipher: aes128-ctr MAC: hmac-sha2-256 compression: none
debug1: kex: client->server cipher: aes128-ctr MAC: hmac-sha2-256 compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: SSH2_MSG_KEX_ECDH_REPLY received
debug1: Server host key: ssh-rsa SHA256:vdFXJflh1ltg2QQ6A8S5qnjtPBtKR3h6l548DAh6Hwk
debug3: put_host_port: [192.168.xxx.xxx]:9999
debug3: put_host_port: [192.168.xxx.xxx]:9999
debug3: record_hostkey: found key type RSA in file /Users/myuser/.ssh/known_hosts:4
debug3: load_hostkeys_file: loaded 1 keys from [192.168.xxx.xxx]:9999
debug1: load_hostkeys: fopen /Users/myuser/.ssh/known_hosts2: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts: No such file or directory
debug1: load_hostkeys: fopen /etc/ssh/ssh_known_hosts2: No such file or directory
debug1: Host '[192.168.xxx.xxx]:9999' is known and matches the RSA host key.
debug1: Found key in /Users/myuser/.ssh/known_hosts:4
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey out after 4294967296 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey in after 4294967296 blocks
debug1: Will attempt key: /Users/myuser/.ssh/id_rsa RSA SHA256:XizaS2UPC7m5C37NwgUVI8uPvLBzLINvRSBnpKGkzPE explicit
debug2: pubkey_prepare: done
debug3: send packet: type 5
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug3: start over, passed a different list publickey
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /Users/myuser/.ssh/id_rsa RSA SHA256:XizaS2UPC7m5C37NwgUVI8uPvLBzLINvRSBnpKGkzPE explicit
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
root@192.168.xxx.xxx: Permission denied (publickey).

```

Why trying to solve the issue, I stumbled across the following Ubuntu Bug: [Dropbear initramfs hook creates authorized_keys file in an invalid folder]("https://bugs.launchpad.net/ubuntu/+source/dropbear/+bug/1645555"), which also seems to be discussed here:
[Help request: dropbear permission denied. Out of ideas!]("https://ubuntuforums.org/showthread.php?t=2349341&p=13594752#post13594752")
> The dropbear hook in the initramfs build process puts the authorized_keys file in a folder named root-DHSkw (root- plus a five-letter suffix that changes each time update-initramfs is run). That same hook file then adds the user root to the passed and group file (to facilitate login once dropbear is running). With this setup, if you login as root, dropbear finds no authorized_keys in the /root/.ssh/ directory. If you login as root-xxxxx, that user (root-xxxxx) has no entry in /etc/passwd/. Only root has an entry in /etc/passwd.
Unfortunately, applying the suggested workaround from the Bug report did not help in my case...


Do you have any clue what could be going wrong?


Thanks in advance, sandman

---

### Post by sandman852 on 2022-01-20
[COLOR=#232629][FONT=-apple-system]Well, after almost going crazy because I couldn't figure out why Dropbear won't accept my key, I revisited everything for the 100st time and finally noticed missing hyphens in the authorized_keys file:
[/FONT][/COLOR]```
no-port-forwarding,no-agent-forwarding,no-x11-forwarding,command=**[COLOR=#ff0000]"[/COLOR]**/bin/cryptroot-unlock**[COLOR=#ff0000]"[/COLOR]** ssh-rsa <here-goes-my-ssh-pubkey> myuser@myMBP.local
```

[COLOR=#232629][FONT=-apple-system]Works flawlessly now :-)[/FONT][/COLOR]

---

