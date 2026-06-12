---
title: "SSH Agent admitted failure to sign using the key. Please help me, need ssh."
date: 2014-10-11
forum: General Help
---

### Post by MechaMechanism on 2014-10-11
Agent admitted failure to sign using the key.
Permission denied (publickey).

That's what I get when I try to login to my SSH server.  Sometimes I can login and sometimes not.  ssh-add sometimes work and sometimes not.  I have an encrypted home dir and my keys are thus in /etc/ssh/nate/

I would love to say thank you to the people who could help me with this.

---

### Post by Lars Noodén on 2014-10-11
What is the exact error from ssh?  It might help to also use a more verbose mode to connect to your server.

```

ssh -v server.example.com

```

Also, on the server, if you have the file *authorized_keys* in /etc/ssh/nate, you need to have a corresponding line added to /etc/ssh/sshd_config to set the location for [AuthorizedKeysFile](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) if that's not there already.

```

AuthorizedKeysFile    /etc/ssh/%u/authorized_keys

```

Also, there should not be two *AuthorizedKeysFile* lines in the file, just one.

---

### Post by MechaMechanism on 2014-10-11
> **Lars Noodén said:**
> What is the exact error from ssh?  It might help to also use a more verbose mode to connect to your server.

```

ssh -v server.example.com

```
Also, there should not be two *AuthorizedKeysFile* lines in the file, just one.

In sshd_config there is only one authorizedkeys line and it's just as you said 
/etc/ssh/%u/authorized_keys> ssh -v @saturn.universal-mechanism.org
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to saturn.universal-mechanism.org [69.146.227.154] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/id_rsa type 1
debug1: identity file /home/user/.ssh/id_rsa-cert type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: identity file /home/user/.ssh/id_dsa-cert type -1
debug1: identity file /home/user/.ssh/id_ecdsa type -1
debug1: identity file /home/user/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/user/.ssh/id_ed25519 type -1
debug1: identity file /home/user/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug1: kex: client->server aes128-ctr [email]hmac-md5-etm@openssh.com[/email] none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA 17:4c:dc:e7:86:4d:6d:90:27:c7:84:79:15:44:61:97
debug1: Host 'saturn.universal-mechanism.org' is known and matches the ECDSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:2
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Ubuntu 14.04.1 LTS
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/user/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 1047
Agent admitted failure to sign using the key.
debug1: Trying private key: /home/user/.ssh/id_dsa
debug1: Trying private key: /home/user/.ssh/id_ecdsa
debug1: Trying private key: /home/user/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).

> # Package generated configuration file
# See the sshd_config(5) manpage for details

AllowUsers user
MaxAuthTries 3
MaxStartups 2:30:10

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel VERBOSE

# Authentication:
LoginGraceTime 30
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile	/etc/ssh/%u/authorized_keys

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
PasswordAuthentication no

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
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
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
UsePAM yes

---

### Post by Lars Noodén on 2014-10-11
The part about it sometimes not working is puzzling.  If you use ssh-add to list the keys it has,

```

ssh-add -l

```

Can you see any difference between when ssh fails and when it works?  Maybe you key is not there, but that is unlikely because Ubuntu snarfs up all the keys it can find whether they are needed or not and that would produce a different error.

---

### Post by MechaMechanism on 2014-10-11
SSH_AUTH_SOCK=0 using that solves the problem.  I filed a bug report.
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1380084](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/1380084)

---

### Post by willianma on 2015-05-15
my notes:
#setting up passwordless ssh for user
#run as user
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
ssh-add


#edit /etc/ssh/sshd_config
#set:
# RSAAuthentication yes
# PubkeyAuthentication yes
# PasswordAuthentication yes 
# PermitRootLogin yes
# AuthorizedKeysFile	%h/.ssh/authorized_keys
# #(set PasswordAuthentication no if really necessary 
# #otherwise users cannot log password)

after, open ANOTHER terminal, and then type ssh-add (don't know why but had to do that in order to work with other terminals..)

---

