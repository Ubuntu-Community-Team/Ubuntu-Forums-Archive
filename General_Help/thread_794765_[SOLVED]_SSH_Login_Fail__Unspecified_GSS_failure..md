---
title: "[SOLVED] SSH Login Fail : Unspecified GSS failure."
date: 2008-05-14
forum: General Help
---

### Post by vi1985 on 2008-05-14
Hi, I have recently updated my openssh-client to v. 1:4.7p1-ubuntu1.2 , and I can no longer login to a remote git repository using my rsa key. Before that, there have been no problems.

I would very much appreciate any help to try and solve the issue! Thank you for taking the time.

I am relatively new to linux, and I don't know how to configure everything just yet, but here is the full report of the problem, and of the solutions I have tried:

First, here is the verbose output:

vitya@vitya-laptop:~$ ssh [email]vi1985@git.thousandparsec.net[/email] -v
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to git.thousandparsec.net [64.251.14.226] port 22.
debug1: Connection established.
debug1: identity file /home/vitya/.ssh/identity type -1
debug1: identity file /home/vitya/.ssh/id_rsa type 1
debug1: identity file /home/vitya/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch1
debug1: match: OpenSSH_4.3p2 Debian-9etch1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'git.thousandparsec.net' is known and matches the RSA host key.
debug1: Found key in /home/vitya/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug1: Next authentication method: gssapi-keyex
debug1: No valid Key exchange context
debug1: Next authentication method: gssapi-with-mic
debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information
No credentials cache found

debug1: Unspecified GSS failure.  Minor code may provide more information


debug1: Next authentication method: publickey
debug1: Offering public key: /home/vitya/.ssh/id_rsa
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug1: Offering public key: 
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug1: Trying private key: /home/vitya/.ssh/identity
debug1: Trying private key: /home/vitya/.ssh/id_dsa
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).


Here is how I tried to remedy the problem:

1) I made sure the public key was in the ~/.ssh/authorized_keys file. Copied it verbatim from the .asc file I exported.

2) set up ssh-agent by entering:

ssh-agent -s
ssh-add

then made sure the key was registered by:
ssh-add -l

Yet nothing seems to help.


The etc/ssh/ssh_config file looks like so:

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
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
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
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

Thank you kindly for your help!!

Victor.

---

### Post by crash369 on 2008-05-15
Probably related to OpenSSH vulnerability/update.

[http://ubuntuforums.org/showthread.php?t=793517](http://ubuntuforums.org/showthread.php?t=793517)

---

### Post by vi1985 on 2008-05-15
Thanks, it turns out that it is.

---

