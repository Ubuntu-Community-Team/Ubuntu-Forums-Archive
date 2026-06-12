---
title: "Running passwordless ssh with sudo"
date: 2017-11-22
forum: General Help
---

### Post by barbeganzi on 2017-11-22
I want to use rsnapshot on a networked machine over ssh. I have generated password-less ssh keys, exported them to the machine using ssh-copy-id, and I'm able to connect the machine without a password using just my normal username. Here's the output for ssh -v on that:
```
OpenSSH_7.2p2 Ubuntu-4ubuntu2.2, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.220 [192.168.1.220] port 22.
debug1: Connection established.
debug1: identity file /home/jason/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/jason/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 192.168.1.220:22 as 'jason'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL]
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: (this is possibly something I don't want published on the internet)
debug1: Host '192.168.1.220' is known and matches the ECDSA host key.
debug1: Found key in /home/jason/.ssh/known_hosts:4
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/jason/.ssh/id_rsa
debug1: Server accepts key: pkalg rsa-sha2-512 blen 279
debug1: Authentication succeeded (publickey).
Authenticated to 192.168.1.220 ([192.168.1.220]:22).
debug1: channel 0: new [client-session]
debug1: Requesting [EMAIL="no-more-sessions@openssh.com"]no-more-sessions@openssh.com[/EMAIL]
debug1: Entering interactive session.
debug1: pledge: network
debug1: client_input_global_request: rtype [EMAIL="hostkeys-00@openssh.com"]hostkeys-00@openssh.com[/EMAIL] want_reply 0
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-101-generic x86_64)
```

I need to run rsnapshot as root, but I keep getting prompted for a password for the user on the remote machine. When I try running sudo ssh -v jason@remotemachineip, here's what I get:

```
OpenSSH_7.2p2 Ubuntu-4ubuntu2.2, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.220 [192.168.1.220] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /root/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
debug1: match: OpenSSH_7.2p2 Ubuntu-4ubuntu2.2 pat OpenSSH* compat 0x04000000
debug1: Authenticating to 192.168.1.220:22 as 'jason'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: algorithm: [EMAIL="curve25519-sha256@libssh.org"]curve25519-sha256@libssh.org[/EMAIL]
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: kex: client->server cipher: [EMAIL="chacha20-poly1305@openssh.com"]chacha20-poly1305@openssh.com[/EMAIL] MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: (once again redacted)
debug1: Host '192.168.1.220' is known and matches the ECDSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<rsa-sha2-256,rsa-sha2-512>
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Trying private key: /root/.ssh/id_ecdsa
debug1: Trying private key: /root/.ssh/id_ed25519
debug1: Next authentication method: password
```

...at which point I'm prompted for the password or rsnapshot fails. It seems to be looking in the wrong place for the keys, but I don't know how to tell it to look in the right place. 

Any help would be amazing. Thanks!

SOLVED

I needed to generate keys for root@startmachine and then export them to user(not root)@remotemachine. One extra step: I had to do ssh-copy-id -i /root/.ssh/key.pub and not simply run the command. It's perfect. It authenticates, but I'm not logged in as root. Someone on Reddit helped me out, but I wanted to share here

---

### Post by SeijiSensei on 2017-11-22
You need to add your credentials to root's ssh configuration on the remote machine.

Copy as root with sudo the contents of /home/username/.ssh/id_rsa.pub on the local machine to the file /root/.ssh/authorized_keys on the remote.  You may need to create /root/.ssh first.  Now you should be able to log in to the remote with the command "ssh -l root remote_hostname_or_ip".

---

