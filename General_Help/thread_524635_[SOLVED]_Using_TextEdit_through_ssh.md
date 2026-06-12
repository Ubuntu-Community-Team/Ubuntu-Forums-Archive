---
title: "[SOLVED] Using TextEdit through ssh"
date: 2007-08-13
forum: General Help
---

### Post by mkramer on 2007-08-13
Hi there.  I've got an Ubuntu 7 distribution installed on my intranet that I am using as a LAMP testbed.  The server is headless and now that it's running fairly reliably I am only accessing it via SSH using Terminal, which is the default Mac OS X terminal.  For a while now I've been using emacs to edit configuration files directly in the terminal. If I were a good linux boy I would only want to use terminal text editors, but I am just not feeling the love. 

What series of commands can I issue to dump the contents of a file into TextEdit (a GUI text editor standard on Macs), and then how can I save the edited buffer back over top of the file on the server?  (And I need to save it as root, because all I ever edit are configuration files).

If it's not possible to do this, how could I take advantage of a GUI text editor on my machine to edit files on the server?

---

### Post by rich.bradshaw on 2007-08-13
Just connect with

ssh -X IPADDRESS

this enables x forwarding, then you can run a gui editor on remote machine, and it will show on mac.

nano is a good terminal editor if that doesn't work - it's simple and easy! might have to apt-get nano to install it, it's only tiny.

---

### Post by mkramer on 2007-08-13
Thanks rich, X11 is a technology I'm not familiar with, but I just looked it up and it seems cool.  Mac has a built in X11 server, so it should work.  I guess the only thing I need to get is  a good GUI text editor for Linux that supports X11  -  do you have any suggestions?  (Something that does code markup would be extra specially cool).

---

### Post by p_quarles on 2007-08-13
The standard Gnome editor is Gedit, which is perfectly decent for basic things, including syntax highlighting. Personally, I prefer SciTE.

---

### Post by mkramer on 2007-08-13
ok I have the X11 server set up on my mac (big-spring), and I installed scite on the client (dark-genius).  
 FIrst I ssh in with
```
big-spring:~ masonkramer$ ssh -X -l mason dg.krm

```

Then I try to run scite

```
mason@dark-genius:~$ scite

(scite:9228): Gtk-WARNING **: cannot open display:  

```.  

I think this means I haven't [enabled X11 forwarding]("http://developer.apple.com/qa/qa2004/qa1383.html") on the client, how do I do that?  (The tute I linked gives instructions for macs, but not linux).
Edit: nevermind, it isn't this issue.  I found the config file and x11forwarding is yes.  Does this error message indicate that I have something wrong with my X11 client, or with my X11 server?

---

### Post by p_quarles on 2007-08-13
Have you enabled x11 forwarding in the server's config file? You'll need to do that first (with a plain old console based text editor):
```
sudo nano /etc/ssh/sshd_config
```

---

### Post by mkramer on 2007-08-13
In both computer's SSH configuration files, ForwardX11 is yes.  However it doesn't work.  Here is a dump.
CLIENT-SIDE SSHD config file (/etc/ssh/sshd_config)
```

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

CLIENT-SIDE  SSH configuration file (/etc/ssh/ssh_config)
```
File Edit Options Buffers Tools Help                                                                                                                      

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
   ForwardX11 yes
   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

SERVER-SIDE (local, the mac) SSH CONFIGURATION FILE (/etc/sshd_config)

```
#       $OpenBSD: ssh_config,v 1.22 2006/05/29 12:56:33 dtucker Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

# Host *
   ForwardAgent yes
   ForwardX11 yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication yes
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange yes
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no

```

Another configuration file I found on the local machine.  (/etc/ssh_config)
```
File Edit Options Buffers Tools Help                                                                                                                                          
#       $OpenBSD: ssh_config,v 1.22 2006/05/29 12:56:33 dtucker Exp $

# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

# Host *
   ForwardAgent yes
   ForwardX11 yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication yes
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange yes
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no

```

What's the difference between ssh and sshd?  On the mac, it appears that one of the two files is a symlink of the other.  On dark-genius, they're different files.  I just said "X11Forwarding Yes" in every file I could find, and it still doesn't work.  

Possibly there is a user-specific config file that is overriding this setting, OR another thought: dark-genius was installed as a server installation.  It doesn't have a desktop environment installed.  Is such a thing necessary?

---

### Post by mkramer on 2007-08-13
A couple hours of Googling has not helped me get through this one.  One thing I did find though is that ```
echo $DISPLAY
``` prints nothing, not 0.0 as somebody seemed to expect.  According to all the documentation I've read, ssh -X is supposed to set all of those environment variables for me.  This command might be of use to someone who is trying to help me: 

```
big-spring:~ masonkramer$ ssh -X -v mason@dg.krm
OpenSSH_4.5p1, OpenSSL 0.9.7l 28 Sep 2006
debug1: Reading configuration data /etc/ssh_config
debug1: Connecting to dg.krm [192.168.123.100] port 22.
debug1: Connection established.
debug1: identity file /Users/masonkramer/.ssh/identity type -1
debug1: identity file /Users/masonkramer/.ssh/id_rsa type -1
debug1: identity file /Users/masonkramer/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: match: OpenSSH_4.3p2 Debian-8ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.5
debug1: Miscellaneous failure
No credentials cache found

debug1: Miscellaneous failure
No credentials cache found

debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'dg.krm' is known and matches the RSA host key.
debug1: Found key in /Users/masonkramer/.ssh/known_hosts:2
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /Users/masonkramer/.ssh/identity
debug1: Trying private key: /Users/masonkramer/.ssh/id_rsa
debug1: Trying private key: /Users/masonkramer/.ssh/id_dsa
debug1: Next authentication method: password
mason@dg.krm's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Requesting X11 forwarding with authentication spoofing.
debug1: Remote: No xauth program; cannot forward with spoofing.
Linux dark-genius.kramer 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686

```

---

### Post by p_quarles on 2007-08-13
Have you restarted the ssh server? 
```
sudo /etc/init.d/ssh restart
```
Once you do that, it should work. If not, I'm not sure what to tell you.

The difference: ssh is the protocol, and the config file of that name configure the client. Sshd (secure shell daemon) is the server software.

---

### Post by mkramer on 2007-08-22
Thank you for your interest p_q, but that doesn't seem to have done the trick.  Can you think of any other reason why I might be receiving the error  ```
(scite:9228): Gtk-WARNING **: cannot open display:
```

---

### Post by p_quarles on 2007-08-22
The only other thing I can think of is that perhaps you haven't installed the GUI software. I figured this would have been added as dependencies when you installed SciTE, but perhaps not. Give this a try (on the server):
```
sudo apt-get install ubuntu-desktop
```
If that doesn't work, well, I'm out of ideas.

---

### Post by mkramer on 2007-08-26
Thanks, that actually seems to have been the problem.  Now it works!

---

### Post by p_quarles on 2007-08-26
Cool. Be sure to mark this thread as "solved," for the benefit of future searchers.

---

