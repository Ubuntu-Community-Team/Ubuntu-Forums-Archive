---
title: "OpenSSH - Permission denied (publickey,password)."
date: 2013-03-19
forum: General Help
---

### Post by ksaul on 2013-03-19
Cant seem to connect to my computer via SSH... been trying to debug this all night but am getting no where...

**when trying to connect....**
> 
ksaul@192:~$ ssh ksaul@192.168.1.110:2323
Ubuntu 12.04.2 LTS

Permission denied (publickey,password).



**/etc/ssh/sshd_config**
> 
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
port 2323
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 1,2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd yes
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

MaxStartups 10:30:60
Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM no
IgnoreUserKnownHosts no
#PasswordAuthentication yes
GatewayPorts no
AllowTcpForwarding yes
KeepAlive yes

**debug info *ssh -v 192.168.1.110***
> 
ksaul@192:~$ ssh -v 192.168.1.110
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: /etc/ssh/ssh_config line 57: Deprecated option "FallBackToRsh"
debug1: Connecting to 192.168.1.110 [192.168.1.110] port 2323.
debug1: Connection established.
debug1: identity file /home/ksaul/.ssh/identity type -1
debug1: identity file /home/ksaul/.ssh/identity-cert type -1
debug1: identity file /home/ksaul/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/ksaul/.ssh/id_rsa-cert type -1
debug1: identity file /home/ksaul/.ssh/id_dsa type -1
debug1: identity file /home/ksaul/.ssh/id_dsa-cert type -1
debug1: identity file /home/ksaul/.ssh/id_ecdsa type -1
debug1: identity file /home/ksaul/.ssh/id_ecdsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.9p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9p1 Debian-5ubuntu1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA e0:d4:b3:0f:c5:82:74:4b:35:a1:81:82:ae:f8:77:e9
debug1: Host '[192.168.1.110]:2323' is known and matches the ECDSA host key.
debug1: Found key in /home/ksaul/.ssh/known_hosts:4
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Ubuntu 12.04.2 LTS

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/ksaul/.ssh/id_rsa
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/ksaul/.ssh/identity
debug1: Trying private key: /home/ksaul/.ssh/id_dsa
debug1: Trying private key: /home/ksaul/.ssh/id_ecdsa
debug1: No more authentication methods to try.
Permission denied (publickey,password).


I have already tried:
- chmod 700 ~/.ssh
- ssh-copy-id ksaul@192.168.1.110
- remaking my ssh keys, via: (1) **ssh-keygen** (2) **ssh-keygen -t rsa** (3) **ssh-keygen -t rsa -b 4096**; all of which I tried with and without a passphrase.


what is wrong with my config?!?!!

---

### Post by markbl on 2013-03-19
I have not checked your config file but, just quickly, apart from "ssh -v" also check the sshd server side log errors, e.g. in /var/log/auth.log. Also, it is not enough to "chmod 700 ~/.ssh", you must also make sure your home area is only writable by you, e.g. "chmod 755 ~", else an "attacker" could move/replace your ~/.ssh dir. Also most of the files in ~/.ssh/* should only be writtable by you, see man sshd.

---

### Post by Cheesemill on 2013-03-19
You can use up to 3 verbose switches with ssh to get a more detailed output, this may help in tracking down the problem...
```
ssh -vvv 192.168.1.110
```

---

