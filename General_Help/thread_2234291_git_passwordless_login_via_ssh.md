---
title: "git passwordless login via ssh"
date: 2014-07-13
forum: General Help
---

### Post by nos09 on 2014-07-13
Hey guys,

I am trying to setup a git server that developers can access without password. 
I am able to access those git repositories with git user's password. I have disabled it now.**Git user doesn't have bash shell, it uses git-shell instead.** But I can't do that with ssh keys somehow. 

I have put my .pub keys into /home/git/.ssh/authorized_keys (git-server)

Some suggested that i should put my private key into .ssh folder and it will automatically gets detected. (which is true cause i can login with root using id_rsa key i generated for that machine).

But when I try I get this 

```
ssh-agent bash -c 'ssh-add /home/x/.ssh/id_rsa; git clone git@git-server:dsp.git'
Enter passphrase for /home/x/.ssh/id_rsa:
Identity added: /home/x/.ssh/id_rsa (/home/x/.ssh/id_rsa)
Cloning into 'dsp'...
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

```
git clone git@git-server:dsp.git
Cloning into 'dsp'...
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

```

Some suggested that i should put my private key into .ssh folder and it will automatically gets detected. (which is true cause i can login with root using id_rsa key i generated for that machine).


Here is my /etc/ssh/sshd_config file : (git-server)

```
cat sshd_config
#       $OpenBSD: sshd_config,v 1.80 2008/07/02 02:24:18 djm Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/local/bin:/bin:/usr/bin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options change a
# default value.

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

# Disable legacy (protocol version 1) support in the server for new
# installations. In future the default will change to require explicit
# activation of protocol 1
Protocol 2

# HostKey for protocol version 1
#HostKey /etc/ssh/ssh_host_key
# HostKeys for protocol version 2
#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_dsa_key

# Lifetime and size of ephemeral version 1 server key
#KeyRegenerationInterval 1h
#ServerKeyBits 1024

# Logging
# obsoletes QuietMode and FascistLogging
#SyslogFacility AUTH
SyslogFacility AUTHPRIV
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
#PermitRootLogin yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      .ssh/authorized_keys
#AuthorizedKeysCommand none
#AuthorizedKeysCommandRunAs nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#RhostsRSAAuthentication no
# similar for protocol version 2
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# RhostsRSAAuthentication and HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
#PasswordAuthentication yes
#PermitEmptyPasswords no
PasswordAuthentication no

# Change to no to disable s/key passwords
#ChallengeResponseAuthentication yes
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no
#KerberosUseKuserok yes

# GSSAPI options
#GSSAPIAuthentication no
GSSAPIAuthentication yes
#GSSAPICleanupCredentials yes
GSSAPICleanupCredentials yes
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
#UsePAM no
UsePAM yes

# Accept locale-related environment variables
AcceptEnv LANG LC_CTYPE LC_NUMERIC LC_TIME LC_COLLATE LC_MONETARY LC_MESSAGES
AcceptEnv LC_PAPER LC_NAME LC_ADDRESS LC_TELEPHONE LC_MEASUREMENT
AcceptEnv LC_IDENTIFICATION LC_ALL LANGUAGE
AcceptEnv XMODIFIERS

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
#X11Forwarding no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PrintMotd yes
#PrintLastLog yes
#TCPKeepAlive yes
#UseLogin no
#UsePrivilegeSeparation yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#ShowPatchLevel no
#UseDNS yes
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none

# no default banner path
#Banner none

# override default of no subsystems
Subsystem       sftp    /usr/libexec/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       ForceCommand cvs server
```

Any help much much appreciated... looking for the solution the whole day, and half night ! ;0 
Thank you.

---

### Post by TheFu on 2014-07-14
TL;DR.
From the client workstation:
* ssh-keygen
* ssh-copy-id (copy-id puts the public key in the correct place, with the correct permissions. ssh is picky about directory/file permissions)

On the server-side, disable password logins. Can't do that until after the ssh-copy-id is done.  NEVER share the private key, only the public key.  All programs that use ssh honor the use of ssh keys and the ~/.ssh/config file.  Know it, use it, love it. Only an ssh port needs to be open, nothing else and it isn't specific to git. ssh is used for all sorts of things ssh, scp, sftp, rsync, rdiff-backup, X forwarding, and ... git.

The **Pro Git** book is free online [http://git-scm.com/book](http://git-scm.com/book) - about 2 pgs in chpt 4 covers setting up a server.

Don't forget to install **fail2ban** everywhere ssh is installed. If your ssh is default, then no other special settings for fail2ban are needed.

---

