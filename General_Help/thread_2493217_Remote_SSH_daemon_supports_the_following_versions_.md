---
title: "Remote SSH daemon supports the following versions of SSH protocol - 1.99, 2.0"
date: 2023-12-07
forum: General Help
---

### Post by ubuuntusgm on 2023-12-07
In Ubuntu 22.04, how to disable SSH protocol support for 1.99

---

### Post by TheFu on 2023-12-07
From the release notes:
```

 * sshd(8): Fix support for client that advertise a protocol version
   of "1.99" (indicating that they are prepared to accept both SSHv1 and
   SSHv2). This was broken in OpenSSH 7.6 during the removal of SSHv1
   support. bz#2810
```

Ref: [https://www.openssh.com/releasenotes.html](https://www.openssh.com/releasenotes.html)

All protocol v1 support was removed in v7.6 of openssh.  22.04 has v8.9.x of openssh, so no v1 support exists anymore.

---

### Post by ubuuntusgm on 2023-12-10
Understood that SSH v1 support was removed. My question is how to disable the support for 1.99

---

### Post by TheFu on 2023-12-11
> **ubuuntusgm said:**
> Understood that SSH v1 support was removed. My question is how to disable the support for 1.99

Get a newer client?  

"1.99" isn't a protocol. It is the way that clients could tell servers that either v1 or v2 protocol versions in ssh were supported and the client + server would negotiate how they'd communicate, so when v1 protocol support was removed, 1.99 became unimportant, effectively making v2 the only supported protocol. 

If you are seeing something different, then it is a bug to be reported.  OpenSSH 7.6 removed all v1 support.  Ubuntu 20.04 has v8.2.x of openssh.

```
$ ssh -V
OpenSSH_8.2p1 Ubuntu-4ubuntu0.9, OpenSSL 1.1.1f  31 Mar 2020

```

From the 'ssh' manpage: 
```
AUTHENTICATION
     The OpenSSH SSH client supports SSH protocol 2.

```

When I connect using ssh to another system with debugging enabled, only protocol 2 is listed, there's no offer of 1.99 provided:
```
debug1: Remote protocol version 2.0, remote software version OpenSSH_8.2p1 Ubuntu-4ubuntu0.9
```

So I'm confused what you think should happen.  ssh doesn't support v0.5 of the protocol either, so there's no need to "disable" it.

---

### Post by MAFoElffen on 2023-12-11
+1 with TheFu --

Previously, you could add lines in the /etc/ssh/sshd_config file, but as TheFu said, after ssh went to a certain version, then support for the SSH-1 protocol was removed altogether, so that was no longer needed.

About that time, ssh keys that were generated as SSH-1 failed. They had to be regen'ed as SSH-2. If that was a problem, you would have hit that problem long ago.

As it is currently, all you have to do and ensure is that all versions of ssh clients and server are updated to current versions (SSH-2). Any other questions about what was before as legacy, just do not apply to what things are, and how they work now. Right?

That is, unless for some nostalgic sake, your goal is to be "insecure" and "vulnerable"... <-- That would not make sense to me.

---

### Post by ubuuntusgm on 2023-12-13
Thanks for the infomations!!
It was false alert from security team.

---

