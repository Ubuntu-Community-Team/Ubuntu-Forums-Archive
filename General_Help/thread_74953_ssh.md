---
title: "ssh"
date: 2005-10-13
forum: General Help
---

### Post by urbanride on 2005-10-13
umm, does ubuntu have an ssh client? or am i just retarded :confused:

---

### Post by Wolki on 2005-10-13
[QUOTE=urbanride]umm, does ubuntu have an ssh client? or am i just retarded :confused:[/QUOTE]

I have ssh, and I'm quite sure i didn't install it manually. If you don't have it for some reason, install openssh-client (with synaptic or apt-get). If you also want the ssh server, install openssh-server, but I would recommend having a good password in that case :)

---

### Post by urbanride on 2005-10-13
well how do you get to your ssh client .. assuming i dont installl openssh

---

### Post by Wolki on 2005-10-13
um... "ssh"?

---

### Post by urbanride on 2005-10-13
well like using secureCRT or PuTTY in windows i can connect to a debain box using ssh ... now i wanna do that from ubuntu.....

sorry im a totaly nix n00b

---

### Post by Wolki on 2005-10-13
[QUOTE=urbanride]well like using secureCRT or PuTTY in windows i can connect to a debain box using ssh ... now i wanna do that from ubuntu.....

sorry im a totaly nix n00b[/QUOTE]

"ssh -l <username> <ip>" is the exact command I think. you need the "-l <username>" only if your current username is different from the one on the machine you want to log into. <ip> is of course the ip of that computer, or alternatively. if it's a named computer, the name.

If you want a gui, there are some, but I don't know about them.

---

### Post by Alexander Kirillov on 2005-10-13
[QUOTE=Wolki]"ssh -l <username> <ip>" is the exact command I think.[/QUOTE]
Or 
ssh [email]username@machine.domain.name[/email]

By the way: it is possible (but not too easy) to set it up so that you do not need to enter a password - by creating a key pair, one half of which is stred on local machine, and the other on remote one. 

Also: if you need secure fle transfer, use "connect to server" in Places menu.

---

### Post by pelago on 2005-10-19
If you want a GUI the Universe repository has PuTTY for Linux (putty package). It doesn't seem to add itself to the Applications menu for some reason.

---

