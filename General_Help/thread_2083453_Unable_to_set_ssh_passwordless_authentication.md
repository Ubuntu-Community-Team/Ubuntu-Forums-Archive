---
title: "Unable to set ssh passwordless authentication"
date: 2012-11-12
forum: General Help
---

### Post by tkota on 2012-11-12
I am unable to ssh with passwordless authentication from Windows client onto UBuntu server. The ssh version on UBuntu is OpenSSH_5.8p1 Debian-7ubuntu1, OpenSSL 1.0.0e , while SSH on Windows Client is OpenSSH_5.1p1, OpenSSL 0.9.8k. I turned on ssh debugging and noticed these messages on server and client:
 
_/usr/bin/sshd -d -p 2222 on server_
 
[COLOR=navy]_adminuser@server:~/.ssh$_ /usr/sbin/sshd -d -p 2222[/COLOR]
[COLOR=navy]debug1: sshd version OpenSSH_5.8p1 Debian-7ubuntu1[/COLOR]
[COLOR=navy]debug1: could not open key file '/etc/ssh/ssh_host_rsa_key': Permission denied[/COLOR]
[COLOR=navy]Could not load host key: /etc/ssh/ssh_host_rsa_key[/COLOR]
[COLOR=navy]debug1: could not open key file '/etc/ssh/ssh_host_dsa_key': Permission denied[/COLOR]
[COLOR=navy]Could not load host key: /etc/ssh/ssh_host_dsa_key[/COLOR]
[COLOR=navy]debug1: could not open key file '/etc/ssh/ssh_host_ecdsa_key': Permission denied[/COLOR]
[COLOR=navy]Could not load host key: /etc/ssh/ssh_host_ecdsa_key[/COLOR]
[COLOR=navy]debug1: setgroups() failed: Operation not permitted[/COLOR]
[COLOR=navy]debug1: rexec_argv[0]='/usr/sbin/sshd'[/COLOR]
[COLOR=navy]debug1: rexec_argv[1]='-d'[/COLOR]
[COLOR=navy]debug1: rexec_argv[2]='-p'[/COLOR]
[COLOR=navy]debug1: rexec_argv[3]='2222'[/COLOR]
[COLOR=navy]Set /proc/self/oom_score_adj from 0 to -1000[/COLOR]
[COLOR=navy]debug1: Bind to port 2222 on 0.0.0.0.[/COLOR]
[COLOR=navy]Server listening on 0.0.0.0 port 2222.[/COLOR]
[COLOR=navy]debug1: Bind to port 2222 on ::.[/COLOR]
[COLOR=navy]Server listening on :: port 2222.[/COLOR]
[COLOR=navy]debug1: Server will not fork when running in debugging mode.[/COLOR]
[COLOR=navy]debug1: rexec start in 5 out 5 newsock 5 pipe -1 sock 8[/COLOR]
[COLOR=navy]debug1: inetd sockets after dupping: 3, 3[/COLOR]
[COLOR=navy]Connection from 10.221.84.65 port 2414[/COLOR]
[COLOR=navy]debug1: Client protocol version 2.0; client software version OpenSSH_5.1[/COLOR]
[COLOR=navy]debug1: match: OpenSSH_5.1 pat OpenSSH*[/COLOR]
[COLOR=navy]debug1: Enabling compatibility mode for protocol 2.0[/COLOR]
[COLOR=navy]debug1: Local version string SSH-2.0-OpenSSH_5.8p1 Debian-7ubuntu1[/COLOR]
[COLOR=navy]debug1: list_hostkey_types: [/COLOR]
[COLOR=navy]No supported key exchange algorithms[/COLOR]
[COLOR=navy]debug1: do_cleanup[/COLOR]
[COLOR=navy]debug1: do_cleanup[/COLOR]
 
_[COLOR=black]ssh -vvv on client[/COLOR]_
[COLOR=#000080]C:\Documents and Settings\clientuser>ssh -vvv -p 2222 [/COLOR][EMAIL="adminuser@server.com"]_[COLOR=#000080]adminuser@server.com[/COLOR]_[/EMAIL]
[COLOR=#000080]OpenSSH_5.1p1, OpenSSL 0.9.8k 25 Mar 2009[/COLOR]
[COLOR=#000080]debug2: ssh_connect: needpriv 0[/COLOR]
[COLOR=#000080]debug1: Connecting to server.com port 2222.[/COLOR]
[COLOR=#000080]debug1: Connection established.[/COLOR]
[COLOR=#000080]debug1: identity file /cygdrive/c/Documents and Settings/clientuser/.ssh/identi[/COLOR]
[COLOR=#000080]ty type -1[/COLOR]
[COLOR=#000080]debug3: Not a RSA1 key file /cygdrive/c/Documents and Settings/clientuser/.ssh/[/COLOR]
[COLOR=#000080]id_rsa.[/COLOR]
[COLOR=#000080]debug2: key_type_from_name: unknown key type '-----BEGIN'[/COLOR]
[COLOR=#000080]debug3: key_read: missing keytype[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug3: key_read: missing whitespace[/COLOR]
[COLOR=#000080]debug2: key_type_from_name: unknown key type '-----END'[/COLOR]
[COLOR=#000080]debug3: key_read: missing keytype[/COLOR]
[COLOR=#000080]debug1: identity file /cygdrive/c/Documents and Settings/clientuser/.ssh/id_rsa[/COLOR]
[COLOR=#000080]type 1[/COLOR]
[COLOR=#000080]debug1: identity file /cygdrive/c/Documents and Settings/clientuser/.ssh/id_dsa[/COLOR]
[COLOR=#000080]type -1[/COLOR]
[COLOR=#000080]debug1: Remote protocol version 2.0, remote software version OpenSSH_5.8p1 Debia[/COLOR]
[COLOR=#000080]n-7ubuntu1[/COLOR]
[COLOR=#000080]debug1: match: OpenSSH_5.8p1 Debian-7ubuntu1 pat OpenSSH*[/COLOR]
[COLOR=#000080]debug1: Enabling compatibility mode for protocol 2.0[/COLOR]
[COLOR=#000080]debug1: Local version string SSH-2.0-OpenSSH_5.1[/COLOR]
[COLOR=#000080]debug2: fd 3 setting O_NONBLOCK[/COLOR]
[COLOR=#000080]debug1: SSH2_MSG_KEXINIT sent[/COLOR]
[COLOR=#000080]Read from socket failed: Connection reset by peer[/COLOR]
I verified that the permissions on authorized_keys, .ssh etc on host are correct. I regenerated host keys to get around the 'Could not load host keys' and restarted ssh services, but problem persists. Here are contents of sshd_config:
[COLOR=#000080]# Package generated configuration file[/COLOR]
[COLOR=#000080]# See the sshd_config(5) manpage for details[/COLOR]
 
[COLOR=#000080]# What ports, IPs and protocols we listen for[/COLOR]
[COLOR=#000080]Port 22[/COLOR]
[COLOR=#000080]# Use these options to restrict which interfaces/protocols sshd will bind to[/COLOR]
[COLOR=#000080]#ListenAddress ::[/COLOR]
[COLOR=#000080]#ListenAddress 0.0.0.0[/COLOR]
[COLOR=#000080]Protocol 2[/COLOR]
[COLOR=#000080]# HostKeys for protocol version 2[/COLOR]
[COLOR=#000080]HostKey /etc/ssh/ssh_host_rsa_key[/COLOR]
[COLOR=#000080]HostKey /etc/ssh/ssh_host_dsa_key[/COLOR]
[COLOR=#000080]HostKey /etc/ssh/ssh_host_ecdsa_key[/COLOR]
[COLOR=#000080]#Privilege Separation is turned on for security[/COLOR]
[COLOR=#000080]UsePrivilegeSeparation yes[/COLOR]
 
[COLOR=#000080]# Lifetime and size of ephemeral version 1 server key[/COLOR]
[COLOR=#000080]KeyRegenerationInterval 3600[/COLOR]
[COLOR=#000080]ServerKeyBits 768[/COLOR]
 
[COLOR=#000080]# Logging[/COLOR]
[COLOR=#000080]SyslogFacility AUTH[/COLOR]
[COLOR=#000080]LogLevel INFO[/COLOR]
 
[COLOR=#000080]# Authentication:[/COLOR]
[COLOR=#000080]LoginGraceTime 120[/COLOR]
[COLOR=#000080]PermitRootLogin yes[/COLOR]
[COLOR=#000080]StrictModes yes[/COLOR]
 
[COLOR=#000080]RSAAuthentication yes[/COLOR]
[COLOR=#000080]PubkeyAuthentication yes[/COLOR]
[COLOR=#000080]#AuthorizedKeysFile %h/.ssh/authorized_keys[/COLOR]
 
[COLOR=#000080]# Don't read the user's ~/.rhosts and ~/.shosts files[/COLOR]
[COLOR=#000080]IgnoreRhosts yes[/COLOR]
[COLOR=#000080]# For this to work you will also need host keys in /etc/ssh_known_hosts[/COLOR]
[COLOR=#000080]RhostsRSAAuthentication no[/COLOR]
[COLOR=#000080]# similar for protocol version 2[/COLOR]
[COLOR=#000080]HostbasedAuthentication no[/COLOR]
[COLOR=#000080]# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication[/COLOR]
[COLOR=#000080]#IgnoreUserKnownHosts yes[/COLOR]
 
[COLOR=#000080]# To enable empty passwords, change to yes (NOT RECOMMENDED)[/COLOR]
[COLOR=#000080]PermitEmptyPasswords no[/COLOR]
 
[COLOR=#000080]# Change to yes to enable challenge-response passwords (beware issues with[/COLOR]
[COLOR=#000080]# some PAM modules and threads)[/COLOR]
[COLOR=#000080]ChallengeResponseAuthentication no[/COLOR]
 
[COLOR=#000080]# Change to no to disable tunnelled clear text passwords[/COLOR]
[COLOR=#000080]#PasswordAuthentication yes[/COLOR]
 
[COLOR=#000080]# Kerberos options[/COLOR]
[COLOR=#000080]#KerberosAuthentication no[/COLOR]
[COLOR=#000080]#KerberosGetAFSToken no[/COLOR]
[COLOR=#000080]#KerberosOrLocalPasswd yes[/COLOR]
[COLOR=#000080]#KerberosTicketCleanup yes[/COLOR]
 
[COLOR=#000080]# GSSAPI options[/COLOR]
[COLOR=#000080]#GSSAPIAuthentication no[/COLOR]
[COLOR=#000080]#GSSAPICleanupCredentials yes[/COLOR]
 
[COLOR=#000080]X11Forwarding yes[/COLOR]
[COLOR=#000080]X11DisplayOffset 10[/COLOR]
[COLOR=#000080]PrintMotd no[/COLOR]
[COLOR=#000080]PrintLastLog yes[/COLOR]
[COLOR=#000080]TCPKeepAlive yes[/COLOR]
[COLOR=#000080]#UseLogin no[/COLOR]
 
[COLOR=#000080]#MaxStartups 10:30:60[/COLOR]
[COLOR=#000080]#Banner /etc/issue.net[/COLOR]
 
[COLOR=#000080]# Allow client to pass locale environment variables[/COLOR]
[COLOR=#000080]AcceptEnv LANG LC_*[/COLOR]
 
[COLOR=#000080]Subsystem sftp /usr/lib/openssh/sftp-server[/COLOR]
 
[COLOR=#000080]# Set this to 'yes' to enable PAM authentication, account processing,[/COLOR]
[COLOR=#000080]# and session processing. If this is enabled, PAM authentication will[/COLOR]
[COLOR=#000080]# be allowed through the ChallengeResponseAuthentication and[/COLOR]
[COLOR=#000080]# PasswordAuthentication. Depending on your PAM configuration,[/COLOR]
[COLOR=#000080]# PAM authentication via ChallengeResponseAuthentication may bypass[/COLOR]
[COLOR=#000080]# the setting of "PermitRootLogin without-password".[/COLOR]
[COLOR=#000080]# If you just want the PAM account and session checks to run without[/COLOR]
[COLOR=#000080]# PAM authentication, then enable this but set PasswordAuthentication[/COLOR]
[COLOR=#000080]# and ChallengeResponseAuthentication to 'no'.[/COLOR]
[COLOR=#000080]UsePAM yes[/COLOR]
Any suggestions on what could be wrong? The host private keys are unable to load because they are owned by 'root' user. Changing their permissions to anything other than mode 600 is not allowed. I appreciate any solutions. I am stuck at this point.. please help!

---

### Post by efflandt on 2012-11-12
Who are you running sshd as.  Normally it would start automatically as root, but if you are running it as a normal user instead, you need some way to set Hostkey file(s) that it can access or maybe using sudo instead. Does **netstat -lnt** still show it listening on port 2222 after the debug ends with do_cleanup?

But it also looks like your client id_rsa file is munged. How did you generate that or get it to the client?  It might not work properly if something word wrapped it (or switched it DOS/Win line endings?).

I always use keys only, with **PasswordAuthentication no** and **PermitRootLogin no** on servers, which always works for me including PuTTY client in Windows. But I have been doing that since somewhere around 1995 (Linux, SunOS, and NetBSD), so I sorted out how to use keys a long time ago.  Not sure why your sshd does not offer password auth when that is enabled, unless the user the server is running as does not have permission to do that either or stops due to no host keys.

---

