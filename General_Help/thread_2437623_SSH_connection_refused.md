---
title: "SSH connection refused"
date: 2020-02-26
forum: General Help
---

### Post by 7-webmaster on 2020-02-26
I have tried to follow all of the instructions for connecting two Ubuntu 19.10 hosts on the same network but the connection fails.

On the "server" machine, actually the laptop whose contents I wish to copy to my desktop, I got the IP address for the local network and added an entry in the  /etc/hosts on the desktop "client".  So jcobban-laptop resolves to 127.0.1.4

On the "server" vsftpd was already installed.  I installed and started openssh-server.  iptables specifies:

```

target        prot opt source      destination
ACCEPT   tcp  --   anywhere  anywhere    tcp dpt:ssh

```
But when I try:

```

sftp -vvvvv jcobban-laptop
OpenSSH_8.0p1 Ubuntu-6build1, OpenSSL 1.1.1c  28 May 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "jcobban-laptop" port 22
debug2: ssh_connect_direct
debug1: Connecting to jcobban-laptop [127.0.1.4] port 22.
debug1: connect to address 127.0.1.4 port 22: Connection refused
ssh: connect to host jcobban-laptop port 22: Connection refused

ssh -vvvvvvv jcobban@jcobban-laptop
OpenSSH_8.0p1 Ubuntu-6build1, OpenSSL 1.1.1c  28 May 2019
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "jcobban-laptop" port 22
debug2: ssh_connect_direct
debug1: Connecting to jcobban-laptop [127.0.1.4] port 22.
debug1: connect to address 127.0.1.4 port 22: Connection refused
ssh: connect to host jcobban-laptop port 22: Connection refused

```

So I am clearly misunderstanding something.  The number of times this particular problem has been reported in this and other forums would suggest that the documentation has room for improvement.  Perhaps this problem could be avoided altogether if the distributed version of Ubuntu came with all of this already installed rather than requiring each user to struggle.

---

### Post by DuckHook on 2020-02-26
ssh-clients are already a part of every 'buntu install. They are configured to work with most setups.

ssh-server, on the other hand, has a high danger potential. If it is misconfigured, it can open your box up to attack from anyone. This is why it is not part of a default install. The assumption is that only people who know what they are doing would want to run a ssh server.

While it cannot be ruled out, your problem is unlikely anything to do with your firewall. Most "Connection refused" problems are ssh-server misconfigurations.

[LIST=1]
[*]Please post the contents of **/etc/ssh/sshd_config** taking care to blank out any sensitive or personally identifying keys (hint: there shouldn't be any personal info on a default install).
[*]Do you use RSA keys for ssh? (You should)
[*]What ssh settings have you tweaked so far? Please be specific, posting actual steps and settings.
[*]You refer to following some reference guides. Which were they?
[/LIST]

---

### Post by TheFu on 2020-02-26
127.x.x.x never leaves the local machine.  Any address that starts with 127 is localhost which means any attempt to connect to some other machine or even a virtual machine using any 127.x.x.x IPs will never work.  No ever.

127.1.6.233  or 127.0.0.1    or 127.99.55.11 or any other IP starting with 127 will always resolve to localhost.  Period.

You need to determine the LAN IP for the machines.
```
ifconfg
ip addr

```will show the LAN IP, if one is setup or gotten from a DHCP server on the network.

---

