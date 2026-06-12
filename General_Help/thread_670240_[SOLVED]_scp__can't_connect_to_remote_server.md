---
title: "[SOLVED] scp:  can't connect to remote server"
date: 2008-01-17
forum: General Help
---

### Post by kenwong on 2008-01-17
I want to use scp to copy files to a remote machine (Windows XP) on which cygwin has been installed for ssh.  I already restarted sshd on that machine with Port 22002.  I have been able to vnc over ssh from my local machine to the remote machine.

However, I cannot connect to the remote machine for scp.

This is the command I use:

scp filename -P 22002 [email]username@url.dyndns.org[/email]:/

After about 3 minutes, I get this message:

ssh: connect to host url.dyndns.org port 22: Connection timed out
lost connection

Any help please?

---

### Post by morgan_greywolf on 2008-01-17
The '-P 2202' has to go first, like this:

```
scp -P 22002 filename username@url.dyndns.org:/
```

HTH

---

### Post by kenwong on 2008-01-17
Thank you very much, morgan_greywolf.

One more question.  Do I need to open any port on my local machine for using scp to copy file to the remote machine?  If yes, can I use ports other than 22?

---

### Post by morgan_greywolf on 2008-01-17
For outgoing connections, you don't need to open any ports.  You only need that for incoming SSH connections on the local machine.  And, yes, you can use any port you like, you just specify it in sshd_config.

---

