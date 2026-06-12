---
title: "Slow SSH connection"
date: 2014-09-30
forum: General Help
---

### Post by lynwode on 2014-09-30
Howdy Folks,
Got a really annoying problem with SSH connections between servers..... its taking a good 10seconds for the password prompt to appear. This is happening between all hosts on the lan. 

```
ssh -vvv user@server 
```

The connection hangs for 10 seconds here:
```
... lots of stuff....
debug2: key: /root/.ssh/id_rsa ((nil)),
debug2: key: /root/.ssh/id_dsa ((nil)),
debug2: key: /root/.ssh/id_ecdsa ((nil)),
debug2: key: /root/.ssh/id_ed25519 ((nil)),

```

and the continues after 10 seconds:
```
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug3: no such identity: /root/.ssh/id_rsa: No such file or directory
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /root/.ssh/id_ecdsa
debug3: no such identity: /root/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /root/.ssh/id_ed25519
debug3: no such identity: /root/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password

```
What may be causing this hold up? I have tried "UseDNS no" and that made no difference. I have also turned off the DNS service and still no difference....
Also no difference between server name and IP address.
Surely a 10sec delay is not normal !

Any help would be appreciated.
Cheers,
Tim.

---

### Post by tgalati4 on 2014-09-30
On the server that you are logging into how many entries (lines) are in the /.ssh/known_hosts file?  It's possible that if you have a lot of entries, that it takes time to go through all of them.  It also appears that the computer that you are using to ssh into your server does not have a properly registered public key, so it defaults to password authentication.  That can take some time.  You can fix it by putting the keys in the correct places:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

[http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login](http://askubuntu.com/questions/46930/how-can-i-set-up-password-less-ssh-login)

It's also possible that you have Landscape or some other process running that takes a while to update it's Message of the Day (motd).  That is the message that is displayed when you first log in.  When you log in, what is the first thing you see on the screen in a terminal?

---

### Post by Lars Noodén on 2014-09-30
What does /etc/ssh/sshd_config on the target host have for *AuthenticationMethods*?

If it is set to anything other than "publickey,password", what is the reason?

---

### Post by btindie on 2014-09-30
I think it's probably down to the "gssapi-keyex,gssapi-with-mic" methods that are enabled on the server.

I get a similar delay when connecting to CentOS servers when that options enabled and just end up disabling it.

If you don't need that method, log into your sever and comment out / disable the GSSAPI options in /etc/ssh/sshd_config then restart sshd.

---

### Post by lynwode on 2014-10-01
There is no "AuthenticationMethods" or "publickey,password" mentioned in any of the sshd_configs on any of the servers and gssapi is set to no on all servers

---

### Post by lynwode on 2014-10-01
I removed all knownhosts from the knownhosts files as I thought that may be a cause but no difference.
There are no messages displayed when I finally login.
I'll take a look at setting up the keys.

---

### Post by Lars Noodén on 2014-10-01
> **lynwode said:**
> There is no "AuthenticationMethods" or "publickey,password" mentioned in any of the sshd_configs on any of the servers and gssapi is set to no on all servers

Ok.  Then you probably have older versions.  Which versions of openssh-server are you running on the machines?  

Maybe there is something in Pluggable Authentication Modules (PAM).  Has /etc/pam.d/sshd been changed from the defaults at all?

---

### Post by lynwode on 2014-10-01
OpenSSH_6.6.1p1 Ubuntu-2ubuntu2, OpenSSL 1.0.1f 6 Jan 2014

I'll take a look at PAM. Although I set UsePAM no to speed up the password authentication.

Maybe I should remove all openssh and reinstall?

---

### Post by Lars Noodén on 2014-10-01
> **lynwode said:**
> OpenSSH_6.6.1p1 Ubuntu-2ubuntu2, OpenSSL 1.0.1f 6 Jan 2014

I'll take a look at PAM. Although I set UsePAM no to speed up the password authentication.

Maybe I should remove all openssh and reinstall?

If you are using OpenSSH_6.6.1p1, then maybe you could try adding a line for authentication methods and see if that speeds things up. 

```

AuthenticationMethods publickey,password

```

I am not sure of the source of the slowdown and doubt that just reinstalling will change anything.  My guess is that it is a configuration issue.  So if you do reinstall, keep backups of config files just in case but get new ones.  Also, be sure to keep the old server keys, otherwise there will be a bit of hassle for your users.

---

### Post by lynwode on 2014-10-01
Ok - I'm now wearing a white cone hat with the word DUNCE on it.....

Just retraced all my steps and added in the UseDNS no again and its now lightning fast..... NFI what I did wrong. 
Anyway thanks for all the help folks !

---

### Post by Lars Noodén on 2014-10-01
Ok.  Glad it's fixed.  The DNS lookup is a common cause of slowness, so no surprise here that it turned out to be the problem here.

---

