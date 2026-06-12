---
title: "Permissions needed to connect via ssh with a remote host"
date: 2013-01-11
forum: General Help
---

### Post by alm on 2013-01-11
Hi.

After creating a "standard" user (with an admin user), the standard user gets this error when trying to connect via ssh with a remote host:

asdf@asdfasdf:~$ ssh remote_user_name@company_server
/bin/bash: line 0: exec: connect: not found
ssh_exchange_identification: Connection closed by remote host

After that, I have "upgrade" the standard user to make it administrator via visudo and with the graphical user admin tool.

Still the problem persists (now if I add "sudo " to the above line, it works).

Now I wonder: What are the permissions needed to connect via ssh with a remote host ?

;)

---

### Post by Muratturat on 2013-01-11
> **alm said:**
> Hi.

After creating a "standard" user (with an admin user), the standard user gets this error when trying to connect via ssh with a remote host:

asdf@asdfasdf:~$ ssh remote_user_name@company_server
/bin/bash: line 0: exec: connect: not found
ssh_exchange_identification: Connection closed by remote host

After that, I have "upgrade" the standard user to make it administrator via visudo and with the graphical user admin tool.

Still the problem persists (now if I add "sudo " to the above line, it works).

Now I wonder: What are the permissions needed to connect via ssh with a remote host ?

;)

[http://ubuntuforums.org/showthread.php?t=1969514](http://ubuntuforums.org/showthread.php?t=1969514)

---

### Post by alm on 2013-01-12
> **Muratturat said:**
> [http://ubuntuforums.org/showthread.php?t=1969514](http://ubuntuforums.org/showthread.php?t=1969514)

Thanks for the answer Muratturat but I can't see your point.
Perhaps I didn`t explain it very well. Let me put it another way:

I am in machine A trying to connect via ssh with machine B.
The problem is that machine A tells me "/bin/bash: line 0: exec: connect: not found".

But when I execute the same ssh command with sudo, it works.

---

### Post by steeldriver on 2013-01-12
Can you ping the company_server without sudo? 

Have you tried starting ssh with the -v (verbose) option to see at what point it is failing?

---

### Post by alm on 2013-01-14
> **steeldriver said:**
> Can you ping the company_server without sudo? 

Have you tried starting ssh with the -v (verbose) option to see at what point it is failing?


Hi.

The destination machine ping is not enabled. I can do telnet to the 22 port and works OK (with and without sudo).

Here is the output of ssh -v:

OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /home/san/.ssh/config
debug1: /home/san/.ssh/config line 7: Applying options for *
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Executing proxy command: exec connect camprsvn200.yelldes.intrayell.com 22
debug1: permanently_drop_suid: 1001
debug1: identity file /home/san/.ssh/id_rsa type 1
/bin/bash: line 0: exec: connect: not found
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/san/.ssh/id_rsa-cert type -1
debug1: identity file /home/san/.ssh/id_dsa type -1
debug1: identity file /home/san/.ssh/id_dsa-cert type -1
debug1: identity file /home/san/.ssh/id_ecdsa type -1
debug1: identity file /home/san/.ssh/id_ecdsa-cert type -1
ssh_exchange_identification: Connection closed by remote host

Here is the output of the id command of the user:

san@gaxmbp:~/bin$ id
uid=1001(san) gid=1001(san) groups=1001(san),4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),104(fuse),106(lpadmin),108(netdev),112(ssh),117(sambashare),118(vboxusers)


Any clue will help.

---

### Post by alm on 2013-01-14
Thank you very much Muratturat and steeldriver !!

It works OK now.

The problem was that the "~/.ssh/" dir was from an older ubuntu instalation.

I am going from installation of kubuntu to a new installation Ubuntu and again to Lubuntu with the same home folder.

I deleted the "~/.ssh/" folder and ssh just recreated it OK.

:popcorn:

---

