---
title: "sshfs stopped working after motherboard change"
date: 2022-08-08
forum: General Help
---

### Post by nlasystems on 2022-08-08
Dear all

I hope someone can solve this mystery for us.
Today our motherboard stopped working and we changed to a new different motherboard and booted the same Ubuntu 14.04 LTS system from the same SSD drive. Everything worked fine except from the fact that a remote pc that used to connect to this pc through the internet with the command below is not connecting any more. It gives [SIZE=+1]read: Connection reset by peer[/SIZE]

sshfs -C -o uid=$USERID,ssh_command='ssh -i ~/.ssh/colKey',workaround=rename noel@nlaUb:/home/nla/software/nladf /usr2

It is pinging OK so the physical connection is still there.

Thanks in advance for any input or ideas.

---

### Post by TheFu on 2022-08-08
14.04 support ended in 2019.  Move to a newer release which has the current versions of ssh.

Also, use  **ssh -vvvv .... ** alone - no sshfs - to troubleshoot ssh connection issues.


But the most important thing you can do is to get off that unsupported release which must have at least 5 remote access flaws at this point in the kernel.  I know there was 1 new flaw this year and one last year. Both were introduced over a decade ago.

---

### Post by coffeecat on 2022-08-08
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by nlasystems on 2022-08-08
Thanks for the reply. Yes I do need to move to a newer release.
But for now we need to solve this problem to be up and running again.
Here is the output of ssh -vvvv ....

col@base:~$ ssh -vvvv nla@nla
OpenSSH_7.2p2 Ubuntu-4ubuntu2.10, OpenSSL 1.0.2g  1 Mar 2016
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "nla" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to nla [777.777.777.777] port 22.
debug1: connect to address 777.777.777.777 port 22: No route to host
ssh: connect to host nla port 22: No route to host

---

### Post by TheFu on 2022-08-08
```
No route to host
```

Fix that.  Could be on this system or any of the network elements between the 2 systems involved.  I'm a little surprised that ping worked, since it shouldn't if there's "no route to host."

---

### Post by nlasystems on 2022-08-09
Found it. Since we changed the mother the Ethernet port is also new and the router assigned the computer a new ip address. Therefore the ssh client was still trying to connect to the old ip.

---

### Post by nlasystems on 2022-08-09
Yes I was surprised too. But now I know why. The router picks the request posted to the public ip (which we were pinging ok) and then forwards this request to the pc's internal ip. That internal ip got changed by the router since we changed the motherboard and therefore the new Ethernet port had a new mac address.

---

