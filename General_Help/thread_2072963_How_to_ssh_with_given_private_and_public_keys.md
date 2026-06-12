---
title: "How to ssh with given private and public keys"
date: 2012-10-18
forum: General Help
---

### Post by clapclash on 2012-10-18
Hi everyone!
I am trying to ssh to a server that already has the the public key and on my machine I already have the private key and the public key.
When I try to connect to the host this is the error I got:

Permission denied (publickey).

I've tried to rename the public key in ~/.ssh/ to authorized_host or to id_rsa.pub but I have always the same problem.
Here the first few lines of the private key:
~snip~

And the public key:
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDYBFP6ihc3Q6U/+rMJO+kgSc9xtcT4HxxjSR10BqJDz3lWnr7YSxmQxbSI7mnKRC+zBvPj9ADphjBm7p27N/08BN6kGqVQbSqYOJ4eeAOC5IzphH9qZBoY+Q7dmXGwR/DcPAXJXPFs62rTUVDPdeB4ZVbNW/j8e/oJuhvJxFZkGHw1QYGoptHItLctS8Kvpgi1ObrT3YxSNZai8cMNoAizEL7V8jxwk3Ep1U3rcK1lHxe1E3X7Wl3Y/+Ww+cb8VZNO29jAuX+wjXbtOElmamvZT5ECbCJXm2kYoWRiSwFeGg2v6MeTjZUZIT98DaKUQLbs+sizwkKNNbd+lMHaXCPZ NCC Graduate Key

I think that either one of them is in the wrong format, but I can't figure it out.
I hope someone of you can help me with this

---

### Post by Lisiano on 2012-10-18
First of all. Don't share your private key.

Second, did you make sure ~/.ssh/ has these permissions (On BOTH machines)?```
lisiano@Lisiano-Ubuntu:~$ ls -lhd ~/.ssh
drwx------ 2 lisiano lisiano 4.0K Aug 17 00:33 /home/lisiano/.ssh
lisiano@Lisiano-Ubuntu:~$ 
```
Next, did you rename your files? Your private keys should stay under their original name (id_dsa or id_rsa)
```
lisiano@Lisiano-Ubuntu:~/.ssh$ ls -lha
total 92K
drwx------   2 lisiano lisiano 4.0K Oct 19 01:38 .
drwxr-xr-x 352 lisiano lisiano  40K Oct 18 23:12 ..
-rw-------   1 lisiano lisiano 2.3K Mar 17  2012 authorized_keys
-rw-------   1 lisiano lisiano  668 Sep 14  2010 id_dsa
-rw-r--r--   1 lisiano lisiano  612 Sep 14  2010 id_dsa.pub
-rw-------   1 lisiano lisiano 1.7K Oct  4  2010 id_rsa
-rw-r--r--   1 lisiano lisiano  404 Oct  4  2010 id_rsa.pub
-rw-------   1 lisiano lisiano  18K Aug 17 08:47 known_hosts
lisiano@Lisiano-Ubuntu:~/.ssh$ 
```
And also are the permissions for your key the same as mine?

Did you append your public key to authorized_keys?

And finally. Are you trying to login as the correct user? For example, I might be lisiano on my local machine, but maybe my server has me under lisiano256, then if I try to login normally via ```
ssh server.ip
```I'd get an error since the user lisiano doesn't exist on the machine, I'd need to connect this way instead ```
ssh lisiano256@server.ip
```

P.S. You can also copy your public key using ssh-copy-id
```
ssh-copy-id server.ip
```

P.P.S. On your server, you may also import a public key from launchpad if you uploaded it there, like this
```
ssh-import-id lisiano256
```

---

### Post by clapclash on 2012-10-18
Thank you Lisiano for the quick reply!
About the first point, I know that I don't have to share the private key but I did it just because I wanted to be sure that the format was ok.
I followed everything you said and now instead before "Permission denied (publickey)" I get a request for the passphrase:
Enter passphrase for key '/root/.ssh/id_rsa': 
debug2: no passphrase given, try next key
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey).

I just press enter because there's no password for connecting to the server.
And this is my /etc/ssh/sshd_config:
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
PermitEmptyPasswords yes

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication yes

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
UseDNS no
```

any ideas?

---

### Post by Lisiano on 2012-10-18
You used a passphrase when you created your key, you need to type that passphrase each time you wish to use the key. If you don't wish to use a passphrase, you will have to modify the key and unset the passphrase.

The only difference a passphrase will make is that if someone gets ahold of your private key, they won't be able to use it.
It won't make a difference when communicating with a server though.

To change the passphrase or to remove it entirely, use this command
```
ssh-keygen -p
```

P.S. Next time, use [noparse]```
these tags so it's easier to navigate long dumps
```[/noparse]```
these tags so it's easier to navigate long dumps
```

---

### Post by efflandt on 2012-10-18
PS: The quick and easy way to wrap formatted text (columns and spaces) with code tags to keep it formatted, and limit its size in a post with scroll bars, is to highlight the formatted text and click **#** in the message window.

---

### Post by clapclash on 2012-10-18
Lisiano I din't create my keys, they were given to me(public and private) and with these keys I need to connect to the server. I don't even know what's the passphrase, all I know is that the private key starts like this:
~snip~

and then you got the key

---

### Post by Lisiano on 2012-10-18
If you received the keys from someone, you will need to request from that same person to give you the passphrase, or you could generate your own keychain and provide the said person with the public key so they may add you.

P.S. I would not use this key for any other purpose beside connecting to that machine. If I were you, I'd append my own public key on that machine as soon as I got access so that I could access that machine knowing I'm not using a compromisable key.

---

### Post by CharlesA on 2012-10-18
Hi,

I snipped the chunk of the private key that you posted.

Your best bet would be to contact the person you got the key from because it has a passphrase attached to it and you won't be able to use it unless you know the passphrase.

Ninja'd by Lisiano ;)

---

