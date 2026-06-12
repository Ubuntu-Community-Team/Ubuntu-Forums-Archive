---
title: "openssh-server stopped working"
date: 2008-05-26
forum: General Help
---

### Post by aeleneski on 2008-05-26
Now I haven't tried connecting to my box for a while. I upgraded from 7.10 to 8.04 a few weeks ago. The last time I tried was sometime before that. But now when I am trying to connect to my box from the outside I get

ssh: connect to host *.net port 22: Connection refused


This used to work. I also notice that if I try ssh localhost, I am able to connect. On my router, I do have it setup so my computer is exposed outside. What could be the cause of this?

---

### Post by rampageoberon on 2008-05-26
Have you checked that it is not being blocked by the firewall?

---

### Post by tamoneya on 2008-05-26
what happens when you try to ping your computer.  What happens when you do a scan on your computer with nmap.

---

### Post by sparrowkc on 2008-05-26
Firstly I would power cycle the router/modem, and secondly I would try Connecting the computer directly to your modem. I can confirm that ssh works for me with 8.04.
Here is my sshd_config from /etc/ssh
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
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
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
```

---

### Post by Eric the Red on 2008-05-26
Hopefully someone didn't hack your system.. Did you updates your OpenSSH server in the last few days? A vulnerability was found that effects most Ubuntu users.

[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)

---

### Post by Monicker on 2008-05-26
> **Eric the Red said:**
> Hopefully someone didn't hack your system.. Did you updates your OpenSSH server in the last few days? A vulnerability was found that effects most Ubuntu users.

[http://www.ubuntu.com/usn/usn-612-2](http://www.ubuntu.com/usn/usn-612-2)


EDIT: Your new link is more relevant than the "daily" tech one.  :P

---

### Post by Eric the Red on 2008-05-26
> **Monicker said:**
> EDIT: Your new link is more relevant than the "daily" tech one.  :P

Yea.. I tend to go there wayyy to much... and why isn't something as important as this not stickied?

---

### Post by Monicker on 2008-05-26
> **Eric the Red said:**
> Yea.. and why isn't something as important as this not stickied.

Actually, it is, in at least 3 different places that I can see.

** glances up at the blue Announcement in General Help**

---

### Post by Eric the Red on 2008-05-26
> **Monicker said:**
> Actually, it is, in at least 3 different places that I can see.

** glances up at the blue Announcement in General Help**

Must be wayy too late... didn't notice that blue text! Pretty neat.

---

