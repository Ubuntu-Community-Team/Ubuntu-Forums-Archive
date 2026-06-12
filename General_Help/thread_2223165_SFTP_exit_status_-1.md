---
title: "SFTP exit status -1"
date: 2014-05-09
forum: General Help
---

### Post by alexeyum on 2014-05-09
Hi everyone!

I am trying to connect to a server via sftp and it fails. Here is the output (removed information about host/login):

```

$ sftp -v -oPort=22 login@example.com
OpenSSH_5.9p1 Debian-5ubuntu1.3, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to example.com [****] port 22.
debug1: Connection established.
debug1: identity file /home/alexey/.ssh/id_rsa type -1
debug1: identity file /home/alexey/.ssh/id_rsa-cert type -1
debug1: identity file /home/alexey/.ssh/id_dsa type -1
debug1: identity file /home/alexey/.ssh/id_dsa-cert type -1
debug1: identity file /home/alexey/.ssh/id_ecdsa type -1
debug1: identity file /home/alexey/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 FreeBSD-20080901
debug1: match: OpenSSH_5.1p1 FreeBSD-20080901 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1.3
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: DSA ****
debug1: Host 'example.com' is known and matches the DSA host key.
debug1: Found key in /home/alexey/.ssh/known_hosts:1
debug1: ssh_dss_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,keyboard-interactive
debug1: Next authentication method: publickey
debug1: Trying private key: /home/alexey/.ssh/id_rsa
debug1: Trying private key: /home/alexey/.ssh/id_dsa
debug1: Trying private key: /home/alexey/.ssh/id_ecdsa
debug1: Next authentication method: keyboard-interactive
Password:
debug1: Authentication succeeded (keyboard-interactive).
Authenticated to example.com ([****]:22).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = ru_RU.UTF-8
debug1: Sending subsystem: sftp
debug1: client_input_channel_req: channel 0 rtype exit-signal reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 2032, received 2352 bytes, in 0.1 seconds
Bytes per second: sent 18967.4, received 21954.4
debug1: Exit status -1
Connection closed

```

I googled this problem, and the common solution is to remove some lines from .bashrc file. However commenting out the complete file didn't work for me.

Can you help me with this problem?

---

### Post by TheFu on 2014-05-09
I'd guess the issue is with the directory/file permissions on the remote system.  On the remote machine, ~/.ssh/ must be 700 and most files inside it must be 600 - except the .pub files, which should be 644.

Also - there is no need to specify the default port for ssh/scp/sftp connections. 22 is the default.

Of course, you probably don't own "example.com" - so that will never work. ;)

---

### Post by GeorgeLSpencer on 2014-05-09
The LANG variable is probably coming from your environment, and may be causing problems with a server not setup for the language specified by ru_RU. Try exporting the value immediately before you sftp to the server; e.g. export LANG=en_US

Also try multiple v's in the parameters, some versions of sftp and ssh will accept -vvv which is very verbose output, but is useful for debugging.

---

### Post by alexeyum on 2014-05-10
Thank you for the answers!

> 
The LANG variable is probably coming from your environment, and may  be causing problems with a server not setup for the language specified  by ru_RU. Try exporting the value immediately before you sftp to the  server; e.g. export LANG=en_US

I've tried this, but it didn't help.

> 
I'd guess the issue is with the directory/file permissions on the  remote system.  On the remote machine, ~/.ssh/ must be 700 and most  files inside it must be 600 - except the .pub files, which should be  644.

Since I don't have shell access to the host, I've had to persuade the hosting support to work on this (originally they said that the problem was with my computer). They've made some changes and now everything is working (not sure if the problem was with .ssh).

---

