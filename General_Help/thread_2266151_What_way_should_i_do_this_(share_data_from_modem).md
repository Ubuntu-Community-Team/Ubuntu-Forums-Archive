---
title: "What way should i do this (share data from modem)"
date: 2015-02-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-02-20
I just got a usb 57k modem, i want to use this for caller id on one system then send the info to other systems on my network and display it using the [FONT=courier new]notify-send[/FONT] command
i have verified i can get the info i want from the modem via [FONT=courier new]/dev/ttyACM0[/FONT]
i figured i would use ssh to send the command, but the authentication process takes way too long (5-7 seconds)
so i figure i can dump the data to a file and fetch it via curl from the client systems, but is there a better way?

---

### Post by TheFu on 2015-02-20
5-7 sec seems way longer than in should. I'd fix that.  Turn up the logging for ssh on the client and server to see why it isn't 2sec or less. There's also autossh which can help with stuff like this or sshfs.  I wouldn't dump security even if it isn't mandatory.

---

### Post by pqwoerituytrueiwoq on 2015-02-20
The bold line is what takes a long time
```
chad@M4A79XTD-EVO:~$ time ssh -vvv pi@10.0.0.25 exit
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.0.0.25 [10.0.0.25] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/chad/.ssh/id_rsa" as a RSA1 public key
debug1: identity file /home/chad/.ssh/id_rsa type 1
debug1: identity file /home/chad/.ssh/id_rsa-cert type -1
debug1: identity file /home/chad/.ssh/id_dsa type -1
debug1: identity file /home/chad/.ssh/id_dsa-cert type -1
debug1: identity file /home/chad/.ssh/id_ecdsa type -1
debug1: identity file /home/chad/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/chad/.ssh/id_ed25519 type -1
debug1: identity file /home/chad/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.0p1 Debian-4+deb7u2
debug1: match: OpenSSH_6.0p1 Debian-4+deb7u2 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "10.0.0.25" from file "/home/chad/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/chad/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,ssh-dss
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
debug1: Server host key: RSA [snip]
debug3: load_hostkeys: loading entries for host "10.0.0.25" from file "/home/chad/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/chad/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host '10.0.0.25' is known and matches the RSA host key.
debug1: Found key in /home/chad/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
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
debug2: key: /home/chad/.ssh/id_rsa (0x7fa838a7b7a0),
debug2: key: chad@M4A79XTD-EVO (0x7fa838a80110),
debug2: key: /home/chad/.ssh/id_dsa ((nil)),
debug2: key: /home/chad/.ssh/id_ecdsa ((nil)),
debug2: key: /home/chad/.ssh/id_ed25519 ((nil)),
**debug1: Authentications that can continue: publickey,password**
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/chad/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp [snip]
debug3: sign_and_send_pubkey: RSA [snip]
debug1: Authentication succeeded (publickey).
Authenticated to 10.0.0.25 ([10.0.0.25]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: packet_set_tos: set IP_TOS 0x08
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug3: Ignored env XDG_VTNR
debug3: Ignored env XDG_SESSION_ID
debug3: Ignored env SELINUX_INIT
debug3: Ignored env XDG_GREETER_DATA_DIR
debug3: Ignored env CLUTTER_IM_MODULE
debug3: Ignored env SESSION
debug3: Ignored env GPG_AGENT_INFO
debug3: Ignored env GLADE_PIXMAP_PATH
debug3: Ignored env SHELL
debug3: Ignored env XDG_MENU_PREFIX
debug3: Ignored env TERM
debug3: Ignored env WINDOWID
debug3: Ignored env UPSTART_SESSION
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env XDG_SESSION_PATH
debug3: Ignored env GLADE_MODULE_PATH
debug3: Ignored env XDG_SEAT_PATH
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env QT_IM_MODULE
debug3: Ignored env JOB
debug3: Ignored env PWD
debug3: Ignored env XMODIFIERS
debug3: Ignored env GNOME_KEYRING_PID
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GDM_LANG
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env IM_CONFIG_PHASE
debug3: Ignored env GDMSESSION
debug3: Ignored env SESSIONTYPE
debug3: Ignored env SHLVL
debug3: Ignored env XDG_SEAT
debug3: Ignored env HOME
debug3: Ignored env LANGUAGE
debug3: Ignored env UPSTART_INSTANCE
debug3: Ignored env UPSTART_EVENTS
debug3: Ignored env LOGNAME
debug3: Ignored env QT4_IM_MODULE
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env INSTANCE
debug3: Ignored env UPSTART_JOB
debug3: Ignored env TEXTDOMAIN
debug3: Ignored env XDG_RUNTIME_DIR
debug3: Ignored env DISPLAY
debug3: Ignored env GLADE_CATALOG_PATH
debug3: Ignored env XDG_CURRENT_DESKTOP
debug3: Ignored env GTK_IM_MODULE
debug3: Ignored env LESSCLOSE
debug3: Ignored env TEXTDOMAINDIR
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug1: Sending command: exit
debug2: channel 0: request exec confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: exec request accepted on channel 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug2: channel 0: rcvd eow
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: rcvd close
debug3: channel 0: will not send data after close
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug3: channel 0: status: The following connections are open:
  #0 client-session (t4 r0 i3/0 o3/0 fd -1/-1 cc -1)

Transferred: sent 3360, received 2248 bytes, in 0.1 seconds
Bytes per second: sent 62089.1, received 41540.6
debug1: Exit status 0

real    0m5.379s
user    0m0.012s
sys    0m0.020s
```

---

