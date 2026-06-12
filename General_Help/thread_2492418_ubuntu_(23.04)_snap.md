---
title: "ubuntu (23.04) snap"
date: 2023-11-10
forum: General Help
---

### Post by fadder on 2023-11-10
I'm trying to run rsync to transfer big files on a remote server, but the command is timed out. Some googling ([here]("https://www.tecmint.com/client_loop-send-disconnect-broken-pipe/")) suggested that I need to increase the SSH connection timeout, and suggested modifying /etc/ssh/sshd_config, but this file doesn't exist. I see loads of such files in many snap directories however, e.g. /snap/core20/1974/etc/ssh/sshd_config or /snap/core22/864/usr/share/openssh/sshd_config. 

How do I increase the timeout parameter when ssh is a snap system? Thanks.

---

### Post by ian-weisser on 2023-11-10
Since we seem to be talking about an Ubuntu Core system (but you could be more clear about that), theoretically you should be able to use "sudo snap get sshd <setting>" and "sudo snap set sshd <setting> <value>"
However, I don't have a Core machine handy at the moment to work out the correct syntax.

---

### Post by MAFoElffen on 2023-11-10
Some Admins set ssh timeouts to reset hung connections in their ~/.ssh/ssh_config, which you can override in the command string... Which you can pass in the rsync command string... Try something like this, adapting it to the rsync options you are using:
```

rsync -avzhe 'ssh -o ServerAliveInterval=0 -o ServerAliveCountMax=0' ' local/dir/files your_user@remote:/destination/ 

```

---

### Post by fadder on 2023-11-13
Thanks for the replies.

@ian-weisser - I am not sure what an Ubuntu core system is. I'm running cinammon 23.04. Your commands didn't work, however:

[INDENT]sudo snap get sshd ServerAliveInterval
[sudo] password for XXXXX: 
error: invalid option name: "ServerAliveInterval"[/INDENT]

@MAFoElffen - those options are accepted, so I'll use that system in future. Thanks.

---

