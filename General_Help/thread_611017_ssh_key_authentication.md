---
title: "ssh key authentication"
date: 2007-11-12
forum: General Help
---

### Post by z662 on 2007-11-12
I have spent the past few days trying to get my server to authenticate with RSA keys for ssh, however i cannot get it to actually use them.  Everytime I go to sign in, it just asks for the password and doesnt mention anything about the keys.  I have read many posts on this forum about the topic and have changed my sshd.conf file to every way I can think of, yet no luck. Heres my sshd.conf file.  Any help would be greatly appreciated!  I also should say I already made the keys and have them in the right place e.g. authorized_hosts

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
ServerKeyBits 2048

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys

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

---

### Post by Brucevdk on 2007-11-13
Config looks ok. If you disabled password authentication it shouldn't ask for a password, did you restart sshd (sudo /etc/init.d/ssh restart)? Try following this guide: [http://www.linux.com/articles/34958](http://www.linux.com/articles/34958)

Also there's an excellent front-end to managing SSH/PGP etc. keys, it's called seahorse (sudo apt-get install seahorse). This process is automated through it, right click your key and select "Set Up Computer for Secure Shell".

---

### Post by bdean42 on 2008-07-21
I am having this same problem. I have two machines, one upgraded several times Feisty > Gusty > Hardy and the other running a freshly installed Hardy.

The machine that has gone through the upgrades is using the ~/.ssh/authorized_hosts file with no problems. I can ssh into that machine and it uses the keys every time. However the newly installed Hardy machine cannot use the authorized_keys at all. I've followed every guide I can think of on this. It's a fairly straightforward procedure so I have no idea why it isn't working. I even copied the /etc/ssh/sshd_config file from the machine that is successfully using authorized_hosts and I restarted the ssh server and still the same thing, it keeps asking for the password every time. I've tried generating new keys and everything, I don't know what the problem is (or even where to look).

---

