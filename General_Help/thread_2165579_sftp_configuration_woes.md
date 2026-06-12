---
title: "sftp configuration woes"
date: 2013-08-05
forum: General Help
---

### Post by scbingham on 2013-08-05
Hello All

I'm running 12.04LTS 32bit server

I've tried setting up sftp but I get this error:

Write failed: Broken pipe
Couldn't read packet: Connection reset by peer

I have read dozens of examples/problems & I feel I am just so close, yet so far away. I'm hoping a fresh pair of eyes & brain will spot the error of my ways.

Feel free to ask for any more info. Thanking you all in advance.


This is from my /etc/passwd:

guestuser:x:1001:1001::/srv/sftp:/sbin/nologin

guestuser is in group sftpusers

This is my directory structure:

/srv/sftp/Data
/srv/sftp/Uploads

Directory permissions:

drwxr-xr-x  4 root root  4096 Aug  4 22:52 srv
drwxrwxr-x 7 root root  4096 Aug  4 23:16 sftp
drwxrwxrwx  2 guestuser sftpusers  4096 Aug  4 22:55 Uploads
drwxr-xr-x  2 guestuser sftpusers  4096 Aug  4 22:50 Data

This is my /etc/ssh/sshd_config file:

[/CODE]

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
PermitRootLogin no
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
#PasswordAuthentication no


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
#Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


#Subsystem sftp /usr/lib/openssh/sftp-server    # I took this out
Subsystem sftp internal-sftp            # & added this


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


# Added for chroot jail


Match group sftpusers
    ChrootDirectory /srv/sftp/%u
    ForceCommand    internal-sftp

[/CODE]

---

### Post by scbingham on 2013-08-06
Anybody have any ideas on how to resolve this? I've had a fresh look today & still can't work it out.

Just noticed the 'code' tags didn't work. How are you supposed to do them?

---

### Post by Mikog on 2013-08-06
Try the following tutorial its a good one.
The thing is that its in Dutch but look at the setup.
[http://wiki.ubuntu-nl.org/community/SftpServer](http://wiki.ubuntu-nl.org/community/SftpServer)

I have compared your passwd to mine and why does your guest user state /sbin/nologin?
Have you also set the permission on the directory of the user?
You can also find this on the url on how to set the permissions.

---

### Post by scbingham on 2013-08-06
Hi Mikog, thanks for the link. Having it in Dutch actually helped me focus :-)

My problem was with me having the wrong home directory. All sorted now.

---

### Post by Mikog on 2013-08-07
scbingham can you put the thread as solved.

Kind regards

---

