---
title: "Problem connecting to remote server"
date: 2014-01-27
forum: General Help
---

### Post by persianbraveheart on 2014-01-27
Hello,

I am trying to use SSH to connect to a remote server by using the following command:

 ssh [EMAIL="Bitcoin@96.49.181.133"][remote_username]@[ip address][/EMAIL]

but I keep getting the following error message:

*Permission denied (publickey,password).*

I followed the instructions using the key-based authentication:[https://www.digitalocean.com/community/articles/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu](https://www.digitalocean.com/community/articles/how-to-use-ssh-to-connect-to-a-remote-server-in-ubuntu)


I opened port 22 in my router as well. Here is the sshd_config file:

```
# Package generated configuration file
# See the sshd_config(5) manpage for details

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
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes

#AuthorizedKeysFile    %h/.ssh/authorized_keys

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
PasswordAuthentication yes


# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

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
X11Forwarding no
```

When I set password authentication and pubkeyauthentication to no, the error message changes to *permission denied()*


When I changed "pubkeyauthentation" to no, the error message changed to *permission denied(password)*

---

### Post by justleen on 2014-01-27
Comparing it to my own sshd conf (without the commeted lines):
```

$ cat /etc/ssh/sshd_config |grep -v '#'| sed '/^ *$/d'
AuthorizedKeysFile	.ssh/authorized_keys
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM yes
Subsystem	sftp	/usr/lib/ssh/sftp-server

```
The above allows only keybased authentication. If you want password authentication too, change PasswordAuthentication to yes.

---

