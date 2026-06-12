---
title: "SSH key permission denied"
date: 2013-02-12
forum: General Help
---

### Post by jaawis on 2013-02-12
Hello im trying to secure my ssh to use keys.
But its not working.
 
I did: 
$ mkdir -p ~/.ssh *If it doesn't already exist*$ chmod 700 ~/.ssh$ cd ~/.ssh$ ssh-keygen -t dsa
 
then: $ scp -p id_dsa.pub remoteuser@remotehost:
At that point i need to give a password, but im getting the message: permission denied ?
 
 
this is mij sshdconfig, i really dont understand anything now...
# Package generated configuration file
# See the sshd_config(5) manpage for details# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768# Logging
SyslogFacility AUTH
LogLevel INFO# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yesRSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile %h/.ssh/authorized_keys# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication noMaxAuthTries 10
# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes
# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yesX11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no#MaxStartups 10:30:60
#Banner /etc/issue.net# Allow client to pass locale environment variables
AcceptEnv LANG LC_*Subsystem sftp /usr/lib/openssh/sftp-server# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication. Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

---

### Post by SlugSlug on 2013-02-12
use this guide
[http://paulkeck.com/ssh/](http://paulkeck.com/ssh/)

---

### Post by LewisTM on 2013-02-12
I don't think the -p switch is meant to specify your public key. For scp ([FONT="Courier New"]man scp[/FONT]), it is used to preserve attributes. For ssh, it's used for setting a different port. 

Are you attempting to append your public key to the host's authorized_keys file? The easiest is to use the **ssh-copy-id **utility.

Cheers!

EDIT: Just got why you put the -p there, sorry.

---

### Post by jaawis on 2013-02-12
I tried serverall tutorials but when i want to copy that key i cant login, so the key is not copied.

---

### Post by CaptainMark on 2013-02-12
you can always use other methods to transfer your clients public key to the server, good old fashioned usb copy and paste still works, 

simply put you need to generate a pair of keys on the client and append the contents of the public key from that pair onto the end of ~/.ssh/authorized_keys on the server, I've seen plenty of people lock down the server to only authorized clients before they've transferred the public key to the server therefore locking themselves out

---

