---
title: "SSH Disconnects after a few seconds"
date: 2015-04-29
forum: General Help
---

### Post by Ian_Chilvers on 2015-04-29
Hi,
 
I’ve just set up a new Ubuntu 14.04 server and whenever I SSH to it it disconnects me in seconds if inactive.
 
I’ve done all the changes below, and still it disconnects me.  What have I missed.
 
In the */etc/ssh/ssh_config* file I have the following
 ```

ServerAliveInterval 100
```
 
In the */etc/ssh/sshd_config* file I have the following
 
```
ClientAliveInterval 600
TCPKeepAlive yes
ClientAliveCountMax 10
```
 
In the */etc/default/ssh* I have changed the SSHD_OPTS to
 
```
SSHD_OPTS='-F /etc/ssh/sshd_config'
```
 
In the *~/.ssh/config* file I have the following
 
```
Host *
ServerAliveInterval 100
```
 
What else do I need to change to stop SSH disconnecting me???
 
Many thanks in advance.

---

### Post by tgalati4 on 2015-04-29
First, check /var/log/auth.log for ssh-related errors.  Post anything useful.  Then comment out your changes and restart *ssh* or reboot.  Also, *ssh* is a classic client/server application, so you need to look at both the client side and server side.  It's possible there is a firewall or router policy that is blocking port 22 and it takes a few seconds to react.

---

### Post by Ian_Chilvers on 2015-04-30
Hi 

Looking at the auth.log sadly didn't give anything away.  Results are below

```

Apr 30 16:50:22 test1 sshd[4179]: Accepted password for testuser from 10.10.10.10 port 43906 ssh2
Apr 30 16:50:22 test1 sshd[4179]: pam_unix(sshd:session): session opened for user testuser by (uid=0)
Apr 30 16:51:35 test1 sshd[4179]: pam_unix(sshd:session): session closed for user testuser

```

Now the SSH session seems to stop working after only 10sec of no typing.  If you keep typing the session stays alive, but with no input or output after 10sec the session stops and a minute later in the auth.log the session is cleared out.

I've tried with or with my settings in place.
I've tried multiple VMs (Basic 14.04 setup with no options selected such as database, web, etc. Just a basic vanilla setup)
I've tried different SSH clients (Putty and also SSH Client from another ubuntu box)

Still the same results.  After 10 seconds it timeouts and you lose the connection.

As for firewall.  I'm running the SSH client on a Windows 8.1 connecting to an Ubuntu VM on the very same box using Bridge Mode.  I've turned the Windows firewall off and still does it.

I don't experience these problems with older ubuntu's using the same SSH client and PC.

I'm clearly missing a setting somewhere but what????

---

### Post by Habitual on 2015-05-01
on the pc that logs you out, check for this environment variable:
```
grep TMOUT .bashrc
``` Is anything returned?

---

### Post by Ian_Chilvers on 2015-05-04
Hi

Nope, nothing to returned after the
```
grep TMOUT .bashrc
```
command

Should there be something?

---

### Post by Habitual on 2015-05-04
> **Ian_Chilvers said:**
> Hi

Nope, nothing to returned after the
```
grep TMOUT .bashrc
```
command

Should there be something?Not necessarily.

---

