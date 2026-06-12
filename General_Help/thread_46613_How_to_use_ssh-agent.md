---
title: "How to use ssh-agent?"
date: 2005-07-05
forum: General Help
---

### Post by yang on 2005-07-05
Hi all, I notice that ssh-agent starts up with Gnome. However, I don't know where its output is saved (I assume it's saved *somewhere* so that new consoles can eval it). Any hints?

---

### Post by EmmEff on 2005-07-07
(From the man page)...

> 
ssh-agent is a program to hold private keys used for public key authenti-
     cation (RSA, DSA).  The idea is that ssh-agent is started in the begin-
     ning of an X-session or a login session, and all other windows or pro-
     grams are started as clients to the ssh-agent program.


You have to add these private keys using 'ssh-add' (or similar way), which are then held by ssh-agent.  When you access a properly configured remote ssh server, the key(s) are automatically used and you won't be prompted for a password.

Use 'ssh-keygen' to generate private and public keys (public key goes on the remote server, private key stays in your local .ssh subdir).

Hope this helps.

---

### Post by yang on 2005-07-11
[QUOTE=EmmEff](From the man page)...

You have to add these private keys using 'ssh-add' (or similar way), which are then held by ssh-agent.  When you access a properly configured remote ssh server, the key(s) are automatically used and you won't be prompted for a password.

Use 'ssh-keygen' to generate private and public keys (public key goes on the remote server, private key stays in your local .ssh subdir).

Hope this helps.[/QUOTE]

Yes, that did: I should've just tried running ssh-add first. To answer my question: apparently the SSH_AUTH_SOCK and SSH_AGENT_PID variables are already set. They are inherited by bash from some parent process (probably gnome-terminal, whose parent is init, and I'm pretty sure init doesn't set SSH_*).

---

### Post by EmmEff on 2005-07-11
I am sure you will find "exec ssh-agent gnome-session" in the startup for GNOME.  That way, the parent of gnome-session is the ssh-agent.  You're all ready to rock & roll by adding keys using ssh-add.

---

