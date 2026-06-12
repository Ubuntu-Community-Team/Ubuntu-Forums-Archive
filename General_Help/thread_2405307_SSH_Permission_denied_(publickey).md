---
title: "SSH Permission denied (publickey)"
date: 2018-11-04
forum: General Help
---

### Post by litu-litu on 2018-11-04
Hi!

I'm sorry if this has been asked before, but I couldn't find a solution and its driving me a bit crazy. I'm trying to ssh into a development Board and I get an error. Then I noticed that it also happens when trying to clone a repository. This is a fresh 18.04 install. SSH on the board works with no problem on my windows partition.

The output of my ssh attempt:

```

ssh robot@192.168.137.3 -vv
OpenSSH_7.6p1 Ubuntu-4, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "192.168.137.3" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to 192.168.137.3 [192.168.137.3] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/lautaro/.ssh/id_ed25519-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.6p1 Ubuntu-4
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4
debug1: match: OpenSSH_7.6p1 Ubuntu-4 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 192.168.137.3:22 as 'robot'
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ssh-ed25519-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
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
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
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
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:a+L+rf+z4YbgZB6k9VhPdJcTy8utjUa4ASGTe32U/+0
The authenticity of host '192.168.137.3 (192.168.137.3)' can't be established.
ECDSA key fingerprint is SHA256:a+L+rf+z4YbgZB6k9VhPdJcTy8utjUa4ASGTe32U/+0.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.137.3' (ECDSA) to the list of known hosts.
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /home/lautaro/.ssh/id_rsa ((nil))
debug2: key: /home/lautaro/.ssh/id_dsa ((nil))
debug2: key: /home/lautaro/.ssh/id_ecdsa ((nil))
debug2: key: /home/lautaro/.ssh/id_ed25519 ((nil))
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/lautaro/.ssh/id_rsa
debug1: Trying private key: /home/lautaro/.ssh/id_dsa
debug1: Trying private key: /home/lautaro/.ssh/id_ecdsa
debug1: Trying private key: /home/lautaro/.ssh/id_ed25519
debug2: we did not send a packet, disable method
debug1: Next authentication method: password
robot@192.168.137.3's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
robot@192.168.137.3's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
robot@192.168.137.3's password: 
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
robot@192.168.137.3: Permission denied (publickey,password).


```

ssh_config file:

```
cat /etc/ssh/ssh_config 

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   IdentityFile ~/.ssh/id_ecdsa
#   IdentityFile ~/.ssh/id_ed25519
#   Port 22
#   Protocol 2
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
#   ProxyCommand ssh -q -W %h:%p gateway.example.com
#   RekeyLimit 1G 1h
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes


```

My sshd_config file

```
cat /etc/ssh/sshd_config 
#    $OpenBSD: sshd_config,v 1.101 2017/03/14 07:19:07 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#PubkeyAuthentication yes

# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile    .ssh/authorized_keys .ssh/authorized_keys2

#AuthorizedPrincipalsFile none

#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none

# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem    sftp    /usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#    X11Forwarding no
#    AllowTcpForwarding no
#    PermitTTY no
#    ForceCommand cvs server


```

output from /var/log/auth.log

```

tail /var/log/auth.log
Nov  4 10:13:32 lautaro-Aspire-V5-591G sshd[4928]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.137.3
Nov  4 10:13:35 lautaro-Aspire-V5-591G sshd[4928]: Failed password for invalid user robot from 192.168.137.3 port 49084 ssh2
Nov  4 10:13:38 lautaro-Aspire-V5-591G sshd[4928]: pam_unix(sshd:auth): check pass; user unknown
Nov  4 10:13:39 lautaro-Aspire-V5-591G sshd[4928]: Failed password for invalid user robot from 192.168.137.3 port 49084 ssh2
Nov  4 10:13:41 lautaro-Aspire-V5-591G sshd[4928]: pam_unix(sshd:auth): check pass; user unknown
Nov  4 10:13:42 lautaro-Aspire-V5-591G sshd[4928]: Failed password for invalid user robot from 192.168.137.3 port 49084 ssh2
Nov  4 10:13:42 lautaro-Aspire-V5-591G sshd[4928]: Connection closed by invalid user robot 192.168.137.3 port 49084 [preauth]
Nov  4 10:13:42 lautaro-Aspire-V5-591G sshd[4928]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.137.3
Nov  4 10:17:01 lautaro-Aspire-V5-591G CRON[4962]: pam_unix(cron:session): session opened for user root by (uid=0)
Nov  4 10:17:01 lautaro-Aspire-V5-591G CRON[4962]: pam_unix(cron:session): session closed for user root

```

I know everything looks a bit empty, but I purged and reinstalled the openssh packages just know in order to clean up the mess I made trying to solve this. If I manually create the keys it still fails and the same happens if I manually add the Users on the ssh_config file. But then again, I may have done it wrong, I'm pretty new to this kind of stuff.

Thanks!!

---

### Post by TheFu on 2018-11-04
**check pass; user unknown**

Is the userid 'robot' in the /etc/passwd file? Does it have a valid password?
If you are trying to login using a remote root account, there are additional settings needed.  It is a terrible idea to allow remote ssh to the root account unless it is extremely locked down.

---

### Post by litu-litu on 2018-11-04
The user is 'robot' indeed. SSH'ing to the same id works on windows, so both the user and password are valid.

---

### Post by The Cog on 2018-11-04
I am confused. Is 18.04 installed on the development board, or on a different computer?

It looks to me as though you are trying to ssh to the same machine. Check your IP addresses. The reason I say this is:
* The command that user lautaro is giving to the ssh client is "ssh robot@192.168.137.3 -vv". So lautaro is trying to**[COLOR="#FF0000"] connect to[/COLOR]** a server on 192.168.137.3 as user robot. It is not immediately clear what IP address the client is on. But...
* The auth.log file shows ```
Nov  4 10:13:32 lautaro-Aspire-V5-591G sshd[4928]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= [COLOR="#FF0000"]rhost=192.168.137.3[/COLOR]
Nov  4 10:13:35 [COLOR="#FF0000"]lautaro-Aspire-V5-591G[/COLOR] sshd[4928]: Failed password for [COLOR="#FF0000"]invalid user robot from 192.168.137.3[/COLOR] port 49084 ssh2
Nov  4 10:13:38 [COLOR="#FF0000"]lautaro-Aspire-V5-591G[/COLOR] sshd[4928]: pam_unix(sshd:auth): check pass; user unknown

``` This auth.log appears to be taken from your laptop. So your laptop is refusing an incoming ssh connection request because it doesn't have a user robot.

It looks to me as though you are connecting from the Aspire laptop to its own IP address (from 192.168.137.3 to 192.168.137.3), not to the development board.

---

### Post by litu-litu on 2018-11-04
18.04 is installed in my laptop. I understand what you say, but the devBoard's IP is 192.168.137.3. I don't understand how can it be that it tries to connect to its own IP.

Anyways, I checked and cleaned the IPv4 settings, manually loaded the MAC and set "*Shared to other computers*". After a reboot it appears to be working now. Let's hope it remains that way.

Thanks!!!

---

### Post by TheFu on 2018-11-04
> **litu-litu said:**
> The user is 'robot' indeed. SSH'ing to the same id works on windows, so both the user and password are valid.

Simple mistakes get everyone.
Have to ask. "ssh_config" and "my sshd_config" isn't clear.  Which is on the client and which is on the server?  And like The Cog asked, are you certain to IP for the SBC is correct?

Moving on, assuming everything is fine above. A common issue is that file permissions aren't correct. Too open or too closed will make ssh fail. Client side and server-side permissions of the ~/.ssh/ area matters.  Some need to be 600 and others need to be 644. Permissions matter and the file system has to support Unix-permissions.

> 
Anyways, I checked and cleaned the IPv4 settings, manually loaded the MAC and set "Shared to other computers". After a reboot it appears to be working now. Let's hope it remains that way.
I have no idea what this means.  IPv4 settings are dirty. As long as the MAC is unique and uses valid characters, it doesn't matter.  ssh will validate the hostname/IP on both sides to avoid MiTM and false-system attacks.

---

### Post by The Cog on 2018-11-04
> **litu-litu said:**
> 18.04 is installed in my laptop. I understand what you say, but the devBoard's IP is 192.168.137.3. I don't understand how can it be that it tries to connect to its own IP.

I think you probably gave the Ubuntu laptop the same IP address as the devBoard, so that it was connecting to itself. You can get Ubuntu to tell you its address with the command **ip addr list**.

---

### Post by TheFu on 2018-11-04
> **The Cog said:**
> I think you probably gave the Ubuntu laptop the same IP address as the devBoard, so that it was connecting to itself. You can get Ubuntu to tell you its address with the command **ip addr list**.

Having 2 devices on the same subnet with the same IP is BAD!
Having 2 devices on the same subnet with the same MAC is BAD!

I'm lazy.  **ip a** is enough or if you want old-school, use **ifconfig**, but that has been deprecated for a few years.

---

### Post by HermanAB on 2018-11-05
It is good that you found and fixed the problem.  In future, if you experience weird network issues, use tcpdump or wireshark and look at the packets.  You will quickly see what is going on.  Don't poke around in the dark - that just wastes time.

My favourite command looks something like this:
$ sudo tcpdump -nlX -i eth0 host 192.168.x.y and port 1234

---

