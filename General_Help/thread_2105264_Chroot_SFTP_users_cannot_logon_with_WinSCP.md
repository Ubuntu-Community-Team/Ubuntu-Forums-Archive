---
title: "Chroot SFTP users cannot logon with WinSCP"
date: 2013-01-15
forum: General Help
---

### Post by ogenrwot on 2013-01-15
I can logon with WinSCP using my username that I have set up for Ubuntu on my home server and access everything I need to. But when [I follow this guide]("http://www.serverubuntu.it/SFTP-chroot") (and several others) I get 
[B]Authenticating with pre-entered password...
Access denied.[/B] 
Here's my SSHD config, what's wrong? I'm bashing my head up against a wall here...

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
AllowUsers *user*
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

PermitEmptyPasswords no

ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

Subsystem sftp internal-sftp

UsePAM no

Match group sftp
  ChrootDirectory /(directory)/(directory)
  ForceCommand internal-sftp
  X11Forwarding no
  AllowTcpForwarding no

---

### Post by ogenrwot on 2013-01-15
It was a permissions issue with OpenSSH. Needed to be set to 755 instead of 775. I'm still trying to figure out how to put flies into their directory so they can access them but for now this is solved.

---

### Post by Resilldoux on 2013-10-01
Even though this is an old thread, I posted a video on YouTube demonstrating this in under 3 minutes: [http://www.youtube.com/watch?v=EQXzyjkLgX0](http://www.youtube.com/watch?v=EQXzyjkLgX0)

---

### Post by Habitual on 2013-10-01
Suggestion:
Doing it in under 3 minutes in a video will scare most (new) users.

Slow down the video...?

But otherwise, good job.

---

