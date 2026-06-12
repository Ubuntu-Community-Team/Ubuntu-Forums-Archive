---
title: "ssh borked to/from 192.168.2.blah"
date: 2007-10-07
forum: General Help
---

### Post by arizonagroovejet on 2007-10-07
So for some reason ssh to/from my Kubuntu (Fiesty) machine no longer works with other machines connected to my router. It used to, now it doesn't. I noticed a few weeks ago but worked around it and forgot about it. Today it's really bugging me. I think I've re-installed since then. I got in a mess trying to use the kernel from Gutsy and lost patience trying to sort it out and just re-installed. (Hurrah for /home on a separate partition!) I'm not 100% sure this was after I noticed the ssh issue but I think it was.

I can ssh from my Kubuntu machine to a system where I work, no problem. I have a virtual machine running  SLED 10 under VMware and a Mac. I can ssh to the virtual machine from the Mac and vica versa. I can't ssh to either of the other two machines from my Kubuntu machine, even if I create a brand new user and l try with that.. I can't ssh in to the Kubuntu machine it from either of the other two machines, even if I try connecting as the newly created user.

I've tried removing the ssh client/server packages and re-installing them. I was using keys to authenticate between the Kubuntu machine and the Mac so I've dumped those I tried disabling IPv6. I've hit Google and found quite a few mentions of this problem but no solution.

ssh from Kubuntu machine to the virtual machine:
```
mike@continuity:~$ ssh -v 192.168.2.5
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.2.5 [192.168.2.5] port 22.
debug1: Connection established.
debug1: identity file /home/mike/.ssh/identity type -1
debug1: identity file /home/mike/.ssh/id_rsa type -1
debug1: identity file /home/mike/.ssh/id_dsa type 2
debug1: Remote protocol version 1.99, remote software version OpenSSH_4.2
debug1: match: OpenSSH_4.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1
debug1: SSH2_MSG_KEXINIT sent
Nothing else happens.

```


sshd output on the Kubuntu machine:
```
mike@continuity:/etc/ssh$ sudo /usr/sbin/sshd -d
debug1: sshd version OpenSSH_4.3p2 Debian-8ubuntu1
debug1: read PEM private key done: type RSA
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
socket: Address family not supported by protocol
debug1: Server will not fork when running in debugging mode.
debug1: rexec start in 4 out 4 newsock 4 pipe -1 sock 7
debug1: inetd sockets after dupping: 3, 3
Connection from 192.168.2.5 port 57158
(I get bored of waiting and hit ctrl C on the machine connecting)
Did not receive identification string from 192.168.2.5
```

ssh used to be fine so why the  $%^*£ does it not work now?

---

### Post by lavinog on 2007-10-07
I don't exactly know the answer to your problem, but I would have to say this looks to be a problem:
```
Server listening on 0.0.0.0 port 22.
socket: Address family not supported by protocol
```

I would check your /etc/ssh/sshd_config file for
```
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0

```

my file has # in front of the last line, I would suspect that yours doesn't
maybe you should use grep to check
```
grep -i listenaddress etc/ssh/sshd_config
```

---

### Post by louieb on 2007-10-08
don't know why the from would be borked. But the other day my Router on its own changed the lan IP from 192.168,bla,bla to 10.0,bla.bla.  Of course that screwed up being able to ssh into any PC on the network. Just something to check.

---

### Post by arizonagroovejet on 2007-10-08
```
mike@continuity:~$ grep -i listenaddress /etc/ssh/sshd_config
#ListenAddress ::
#ListenAddress 0.0.0.0
mike@continuity:~$
```


```

mike@continuity:~$ ifconfig | head -2
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:96:DB:36
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
```


Bah!

---

### Post by lavinog on 2007-10-10
have you tried to disable any firewalls and see if it works?

try:
> sudo iptables -L
see if any ports are being dropped?

---

### Post by arizonagroovejet on 2007-10-22
Got bored of looking at the problem, installed Gusty, no more problem.

---

