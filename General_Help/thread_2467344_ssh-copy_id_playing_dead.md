---
title: "ssh-copy_id playing dead"
date: 2021-09-23
forum: General Help
---

### Post by Old Jimma on 2021-09-23
Hello Ubuntuers:

I'm trying to set up an ssh public key... and am having a problem:

I start the process by issuing:

$ ssh-keygen

... and then just keep hitting return the process ends.

Then, I check to make sure there is an .ssh directory in my home directory, and that it has the 2 files: id_rsa and id_rsa.pub

After that,  i ussue the following command to  share the keys 

$ ssh-copy-id username$ipa.ddr.ess

... And then I hit return.

However, the process just hangs there, prints nothing, and an .ssh directory is not put into the /home/username directory for the machnie with ip address: ipa.ddr.ess

ssh-copy-id is playing dead!

Usually this work... but its stalled now.

What can I do to fix this??

Old Jim

---

### Post by Old Jimma on 2021-09-23
I figured it out.

In order for > 
ssh-copy-id username$ipa.ddr.ess

to work, ssh must be allowed to work on the machine with home > /home/username[QUOTE] and ipaddress [QUOTE]ipa.ddr.ess.

Here is a url that shows how to do that: > [https://linuxhint.com/ufw-firewall-allow-ssh/](https://linuxhint.com/ufw-firewall-allow-ssh/)

Old

---

### Post by TheFu on 2021-09-23
```
$ ssh-copy-id username$ipa.ddr.ess
```
is wrong.
It needs to be
```
$ ssh-copy-id username[COLOR="#FF0000"]@[/COLOR]$ipa.ddr.ess
```

Details matter, as always.
The username is only needed if it is different from the username on the current system.
Also, you can setup a ~/.ssh/config file with a stanza for each remote system, so you'll never need to know the IP address or username again.  Trust me. Adding those 4 lines to that file will change your life almost as much as using ssh-keys does.

Why use the inferior RSA keys?  ed25519 should be used. It is more secure.

---

