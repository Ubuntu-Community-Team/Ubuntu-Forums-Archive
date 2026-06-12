---
title: "ssh inaccesible"
date: 2015-07-15
forum: General Help
---

### Post by ruben26 on 2015-07-15
Hi
We have a common configuration for Ubuntu with ssh for the sftp trafick.  The sftp is ok, but i cant ssh the machine.  i used to be able to but i do not know what has happened.
i have checkd all the settings in the config_sshd file and they are fine, but still no joy.
i need to be able to diagnost the problem, and find out the cause.  the ssh server is running, i can restart it and it says is running fine.  it is listening to port 22.
Not sure what else i can do, but this is so anoying because i'm having to go to the server room to work on it, and it is freezing down there :)

many thanks

---

### Post by Lars Noodén on 2015-07-15
Which customizations does this common configuration have in sshd_config?

---

### Post by ruben26 on 2015-07-15
nothing unusual:
[B]PermitRootLogin yes
[B]StrictModes yes
[B]PasswordAuthentication yes
[B]PermitEmptyPasswords no

[/B][/B][/B][/B]I can copy the whole file latter today when i'm in the server room
many thanks**[B][B][B]**[/B][/B]
[/B]

---

### Post by Lars Noodén on 2015-07-15
It might be good to see the whole file. Something is up if you can use sftp but not ssh.  Possibly there is a *ForceCommand* set somewhere.  If there is, you could make a *Match* block to make it affect only certain users or else make an exception for certain users.

---

### Post by ruben26 on 2015-07-16
[COLOR=#a52a2a][/COLOR][COLOR=#a52a2a][/COLOR]Here is the full file.
hope you can help[COLOR=#a52a2a]

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
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin without-password
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
AllowGroups sudo sftponly sftponly-restricted
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

 Subsystem sftp /usr/lib/openssh/sftp-server
# Subsystem sftp internal-sftp
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
# Rules for sftponly group
Match group sftponly
ChrootDirectory %h
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

# Rules for sfptonly-restricted group
Match group sftponly-restricted
ChrootDirectory %h
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp
[/COLOR]



thanks

---

### Post by ruben26 on 2015-07-16
it is fixed now.
the only change i did to the file was to add 'sudo' to the file in the AllowGroups, as you can see up there.  Not sure why this fixed as it was never like that.
any way, many thanks for the help.

---

### Post by Lars Noodén on 2015-07-16
Thanks.  You should be able to connect using ssh with any user that is neither in the group *sfptonly* nor the group *sfptonly-restricted*  There are two Match clauses which force sftp on users in those groups.

If you want to preview which configuration [sshd](http://manpages.ubuntu.com/manpages/trusty/en/man8/sshd.8.html) is using for any particular user, then substitute *destination-ip* and *source-ip* with the corresponding IP numbers of the server and the client.  
 
```

sudo sshd -T -C user=*ruben26*,host=*destination-ip*,addr=*source-ip*

```

---

### Post by Lars Noodén on 2015-07-16
> **ruben26 said:**
> it is fixed now.
the only change i did to the file was to add 'sudo' to the file in the AllowGroups, as you can see up there.  Not sure why this fixed as it was never like that.
any way, many thanks for the help.

Glad it works.  If that's all that was changed, then there's some interesting priorities with groups going on.  I'll have to try some experiments on that to learn.

---

