---
title: "can't apt-get update"
date: 2022-05-10
forum: General Help
---

### Post by chat-4432 on 2022-05-10
when i apt-get update 
it show 
some index files failed to download. they have been inored, or old ones useed instead
when i install tasksel 
it show
unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
how to fix it ??

---

### Post by Frogs Hair on 2022-05-10
Try the suggested command. 

```
sudo apt update --fix-missing
```

Then
 ```
sudo apt install -f

```

---

### Post by Impavidus on 2022-05-10
Can you give the complete error message, instead of just the line stating than an error occured? It may be useful to know which version of Ubutu you use.

---

### Post by chat-4432 on 2022-05-10
> **Frogs Hair said:**
> Try the suggested command. 

```
sudo apt update --fix-missing
```

Then
 ```
sudo apt install -f

```

it show the same problem as apt update

---

### Post by chat-4432 on 2022-05-10
> **Impavidus said:**
> Can you give the complete error message, instead of just the line stating than an error occured? It may be useful to know which version of Ubutu you use.
Ign1:....
Ign2:....
Ign3:....
Ign4:....
repeat

err1 temporary failure resolving'ports.ubuntu.com'
err2 temporary failure resolving'ports.ubuntu.com'
err3 temporary failure resolving'ports.ubuntu.com'
 
E:failed to fetch ....... temporary failure resolving
E:failed to fetch ....... temporary failure resolving
E:failed to fetch ....... temporary failure resolving
E:Unable to fetch some archies maybe run apt-get update or try with --fix-missing?
my ubuntu is 22.04

---

### Post by Holger_Gehrke on 2022-05-10
It's a name resolution problem. One of the first steps in any network connection is resolving names into IP-addresses. For some reason your system can't get an IP for ports.ubuntu.com. Not much you can do about that but wait, it's probably a problem on the DNS-server you're using. As a side note, ports.ubuntu.com is a server holding packages for non-x86 systems (Arm, PowerPC64, RiscV, S390). Unless you're using a processor from one of those families there's no need to have that as a source for packages.

Holger

---

### Post by ActionParsnip on 2022-05-10
Can you ping 8.8.8.8 OK?

---

### Post by chat-4432 on 2022-05-10
> **ActionParsnip said:**
> Can you ping 8.8.8.8 OK?
it show like this
ping: OK: Temporary failure in name resolution

---

### Post by chat-4432 on 2022-05-10
it also show this when i login ubuntu
the list of avaiable update is more than a week old.
to check for new update run: sudo apt update
failed to connect to changelogs.ubuntu.com/meta-release-lts. check your internet connnection or proxy settings

---

### Post by ActionParsnip on 2022-05-11
> **chat-4432 said:**
> it show like this
ping: OK: Temporary failure in name resolution

There is no name resolution to do. It's an IP address. The command is
```

ping -c 4 8.8.8.8

```

Check spacing as you type

---

### Post by chat-4432 on 2022-05-11
> **ActionParsnip said:**
> There is no name resolution to do. It's an IP address. The command is
```

ping -c 4 8.8.8.8

```

Check spacing as you type

ping: connect: Network is unreachable

what should i do??

---

### Post by chat-4432 on 2022-05-29
> **chat-4432 said:**
> ping: connect: Network is unreachable

what should i do??
now i switching it to ssh terminal
it show
```
[CODE]--- 8.8.8.8 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 52.799/57.671/70.655/7.504 ms



```[/CODE]

---

### Post by chat-4432 on 2022-05-29
when I try sudo apt update it shows this for a while
```
0% [Connecting to ports.ubuntu.com (2620:2d:4000:1::19)]
```
and then
```
ubuntu@ubuntu:~$ sudo apt update
Ign:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Ign:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Ign:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Ign:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Ign:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
Ign:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
Ign:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
Ign:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
Err:1 http://ports.ubuntu.com/ubuntu-ports jammy InRelease
  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to ports.ubuntu.com:80 (185.125.190.36), connection timed out Could not connect to ports.ubuntu.com:80 (185.125.190.39), connection timed out
Err:2 http://ports.ubuntu.com/ubuntu-ports jammy-updates InRelease
  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
Err:3 http://ports.ubuntu.com/ubuntu-ports jammy-backports InRelease
  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
Err:4 http://ports.ubuntu.com/ubuntu-ports jammy-security InRelease
  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy/InRelease  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to ports.ubuntu.com:80 (185.125.190.36), connection timed out Could not connect to ports.ubuntu.com:80 (185.125.190.39), connection timed out
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-updates/InRelease  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-backports/InRelease  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
W: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/jammy-security/InRelease  Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Cannot initiate the connection to ports.ubuntu.com:80 (2620:2d:4000:1::16). - connect (101: Network is unreachable)
W: Some index files failed to download. They have been ignored, or old ones used instead.



```
what should i do??

---

### Post by ActionParsnip on 2022-05-30
Does your LAN use IPv6?

---

### Post by chat-4432 on 2022-05-30
> **ActionParsnip said:**
> Does your LAN use IPv6?
no. it IPv4

---

