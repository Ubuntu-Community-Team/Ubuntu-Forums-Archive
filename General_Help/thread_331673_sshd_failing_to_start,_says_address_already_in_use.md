---
title: "sshd failing to start, says address already in use"
date: 2007-01-04
forum: General Help
---

### Post by talz13 on 2007-01-04
I just got finished with a fresh install of 6.10 on my server, and just about everything is going well now.  However, sshd isn't cooperating with me.  I just used synaptic to install the openssh server, and went to start it, and it says it starts, but it doesn't work.

What I mean by that is, I get the [ok] message when I run sudo /etc/init.d/ssh start, but when I go to connect, it won't.

I found some relevant error messages in the auth.log:

```

Jan  4 22:11:50 server sudo:     jeff : TTY=tty1 ; PWD=/home/jeff ; USER=root ; COMMAND=/etc/init.d/ssh stop
Jan  4 22:11:55 server sudo:     jeff : TTY=tty1 ; PWD=/home/jeff ; USER=root ; COMMAND=/etc/init.d/ssh start
Jan  4 22:11:55 server sshd[14535]: error: Bind to port 1081 on 0.0.0.0 failed: Address already in use.
Jan  4 22:11:55 server sshd[14535]: fatal: Cannot bind any address.
Jan  4 22:13:46 server sudo:     jeff : TTY=tty1 ; PWD=/home/jeff ; USER=root ; COMMAND=/etc/init.d/ssh restart
Jan  4 22:13:46 server sshd[14561]: error: Bind to port 1081 on 192.168.1.5 failed: Address already in use.
Jan  4 22:13:46 server sshd[14561]: fatal: Cannot bind any address.

```

I tried changing the listen address to the IP of the machine, but it didn't change anything.  I  run my ssh on a non-default port to cut down on the old script kiddie login attempts I used to get all the time, so 1081 is the right port listed there.

Any idea what could be wrong?

I'll post my sshd config file as well, I guess:
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 1081
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
ListenAddress 192.168.1.5
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
LogLevel VERBOSE

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

### Post by bettlebrox on 2007-01-04
I'd check to see if the ssh daemon is already running:
ps -ef|grep -i ssh

If that's not see if you can figure out what's running on that port. 
sudo netstat -a -p |more

sudo lsof -i tcp |more (or |grep 1080)

---

### Post by talz13 on 2007-01-05
Thanks for the check code.  There was another ssh server running, but apparently it wasn't heeding my calls to stop.  I went in and killed the process and ran start again, and it's working fine now.

---

### Post by bitagenda on 2007-03-21
**My case:**
sshd started twice, so the address was already in use.
Problem: I installed openssh and FreeBSD already has ssh, so you have to use the one you installed which does not replaces (files talking) the FreeBSD ones.
Solution:
1.-  Follow the instructions in the port's pkg-message
2.- Move the file sshd from /etc/rc.d/.. to an archive directory (not one in the PATH), because when you set rc.conf with sshd_enable="YES" this one will start too.
Problem solved.

Bitagenda

---

