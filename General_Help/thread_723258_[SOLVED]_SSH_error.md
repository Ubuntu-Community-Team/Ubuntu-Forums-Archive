---
title: "[SOLVED] SSH error"
date: 2008-03-13
forum: General Help
---

### Post by snorkytheweasel on 2008-03-13
[FONT="Verdana"]I have a remote web server (Red Hat) on which I am Deus ex Machina.

I have 3 workstations: 2 ubuntus run 7.10 :KS :KS, the third runs windxp ](*,)

The xp station and one of the ubus can SSH into the web server without problems.

The other Gutsy workstation  returns this error when I attempt to SSH into the same web server:[/FONT]
[B]
Add correct host key in /home/eljefe/.ssh/known_hosts to get rid of this message.
Offending key in /home/elhefe/.ssh/known_hosts:1
RSA host key for [www.mywebserver.com](www.mywebserver.com) has changed and you have requested strict checking.
Host key verification failed.[/B]

[FONT="Verdana"]How do I un-request strict checking?[/FONT]
and/or
[FONT="Verdana"]How do I determine the correct RSA key for the web server?[/FONT]

---

### Post by finer recliner on 2008-03-13
edit your config file

/etc/ssh/ssh_config

---

### Post by kevdog on 2008-03-13
If you edit the the ssh_config file either in /etc/ssh/ssh_config (which applies to all users on the system) or to your personal ssh_config file (if it exists its in ~/.ssh) you can change the requirement for strict host key checking.

If the key has change you can also edit your ~/.ssh/known_hosts file and delete out the old entry for your server here, so that it will accept the new fingerprint.

---

### Post by snorkytheweasel on 2008-03-13
It turns out the problem was with my local .ssh/known_hosts.

When I emptied that file, the ssh command prompted me to accept the "new" key from the host. I told it to rock on, and everything is fine now.

I wouldn't have figured that out without your clue (and a half-hour of experimenting with /etc/ssh/ssh_config until I got a usable error message).

THX TTFN  \\:D/

---

### Post by snorkytheweasel on 2008-03-13
I wish I'd seen your post sooner. I spent quite a while terrorizing my /etc/ssh/ssh_config until I got an error message that gave the clue I needed - to do exactly what you said.

I appreciate your help.

---

