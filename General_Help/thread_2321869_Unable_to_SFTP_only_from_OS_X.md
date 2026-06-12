---
title: "Unable to SFTP only from OS X"
date: 2016-04-25
forum: General Help
---

### Post by Ian_Graham on 2016-04-25
I am running Ubuntu Server 12.04.5 LTS and I'm having a problem connecting to the SFTP server from OS X. I've tested both on OS X and on Windows and Windows (FileZilla) has absolutely no problems connecting. I've attached the auth logs and verbose client connection output incase anyone can help. Interestingly enough the errors in the auth.log don't seem to effect Windows clients connecting. I have verified the issue is present with multiple OS X devices and not present with multiple windows devices. 

SSH Version: OpenSSH_5.9p1, SSH protocols 1.5/2.0, OpenSSL 0x1000100f

I've confirmed that indeed the /usr/libexec/sftp-server file doesn't exist per the auth.log, and this is referenced in the sshd config file in /etc/. However this doesn't explain why windows clients are still able to connect. If this is an issue with the sftp-server subsystem not being found, why are windows clients able to connect? How would I locate the sftp subsystem and safely update the sshd config file without breaking ssh? There is no /usr/libexec directory in the system. 

Any help is much appreciated.

auth.log output durring connection:

```
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 185
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 186
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 187
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 188
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 189
Apr 24 22:41:29 SERVERNAME sshd[16775]: error: Bad prime description in line 190
Apr 24 22:41:29 SERVERNAME sshd[16775]: Authentication refused: bad ownership or modes for file /home/USERNAME/.ssh/authorized_keys
Apr 24 22:41:41 SERVERNAME sshd[16775]: Accepted password for USERNAME from CLIENTIP port 61790 ssh2
Apr 24 22:41:41 SERVERNAME sshd[16777]: subsystem request for sftp
Apr 24 22:41:41 SERVERNAME sshd[16777]: error: subsystem: cannot stat /usr/libexec/sftp-server: No such file or directory
Apr 24 22:41:41 SERVERNAME sshd[16777]: subsystem request for sftp failed, subsystem not found

```

Client verbose logs:

```
clienthostname:.ssh USERNAME$ sftp -vvv USERNAME@server
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [server] port 22.
debug1: Connection established.
debug1: identity file /Users/USERNAME/.ssh/id_rsa type 1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /Users/USERNAME/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.9
debug1: Remote protocol version 1.99, remote software version OpenSSH_5.9p1
debug1: match: OpenSSH_5.9p1 pat OpenSSH_5* compat 0x0c000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to server:22 as 'USERNAME'
debug3: hostkeys_foreach: reading file "/Users/USERNAME/.ssh/known_hosts"
debug3: record_hostkey: found key type RSA in file /Users/USERNAME/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from server
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,ssh-dss
debug2: kex_parse_kexinit: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1,hmac-md5-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1,hmac-md5-etm@openssh.com,hmac-ripemd160-etm@openssh.com,hmac-sha1-96-etm@openssh.com,hmac-md5-96-etm@openssh.com,hmac-md5,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug1: kex: server->client aes128-cbc hmac-sha1 none
debug1: kex: client->server aes128-cbc hmac-sha1 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<7680<8192) sent
debug1: got SSH2_MSG_KEX_DH_GEX_GROUP
debug2: bits set: 3097/6144
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: got SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: ssh-rsa SHA256:6sTUzf0egh7HmD6GUCQaDkC0cVrrgN6eEF26Plv9fAI
debug3: hostkeys_foreach: reading file "/Users/USERNAME/.ssh/known_hosts"
debug3: record_hostkey: found key type RSA in file /Users/USERNAME/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys from server
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /Users/USERNAME/.ssh/known_hosts:1
debug2: bits set: 3056/6144
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /Users/USERNAME/.ssh/id_rsa (0x7ffb71514260),
debug2: key: /Users/USERNAME/.ssh/id_dsa (0x0),
debug2: key: /Users/USERNAME/.ssh/id_ecdsa (0x0),
debug2: key: /Users/USERNAME/.ssh/id_ed25519 (0x0),
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: start over, passed a different list publickey,password,keyboard-interactive
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /Users/USERNAME/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug1: Trying private key: /Users/USERNAME/.ssh/id_dsa
debug3: no such identity: /Users/USERNAME/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /Users/USERNAME/.ssh/id_ecdsa
debug3: no such identity: /Users/USERNAME/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /Users/USERNAME/.ssh/id_ed25519
debug3: no such identity: /Users/USERNAME/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup keyboard-interactive
debug3: remaining preferred: password
debug3: authmethod_is_enabled keyboard-interactive
debug1: Next authentication method: keyboard-interactive
debug2: userauth_kbdint
debug2: we sent a keyboard-interactive packet, wait for reply
debug1: Authentications that can continue: publickey,password,keyboard-interactive
debug3: userauth_kbdint: disable: no info_req_seen
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: 
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
USERNAME@server's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
Authenticated to server ([server]:22).
debug2: fd 5 setting O_NONBLOCK
debug3: fd 6 is O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IP_TOS 0x08
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug3: Ignored env TERM_PROGRAM
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env TMPDIR
debug3: Ignored env Apple_PubSub_Socket_Render
debug3: Ignored env TERM_PROGRAM_VERSION
debug3: Ignored env TERM_SESSION_ID
debug3: Ignored env USER
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env __CF_USER_TEXT_ENCODING
debug3: Ignored env PATH
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env XPC_FLAGS
debug3: Ignored env XPC_SERVICE_NAME
debug3: Ignored env HOME
debug3: Ignored env SHLVL
debug3: Ignored env LOGNAME
debug3: Ignored env _
debug1: Sending subsystem: sftp
debug2: channel 0: request subsystem confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 100 id 0
subsystem request failed on channel 0
Connection closed
```

---

