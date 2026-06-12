---
title: "SSH Could not resolve hostname"
date: 2013-01-18
forum: General Help
---

### Post by Joao Lacerda on 2013-01-18
Hi friends,

Can maybe someone help with this question?

I am trying to connect to a ubuntu server 12.04,  with ubuntu 12.10, from the terminal and that is the response.

Ssh 192.168.0.xxxx:xxxx
ssh: Could not resolve hostname 192.168.0.xxx:xxxx: Name or service not known

ssh [email]username@192.168.0.xxxx[/email]:xxxxx
ssh: Could not resolve hostname 192.168.0.xxx:xxxx: Name or service not known

It have worked fine when both computers had ubuntu 12.04.

I can connect it with putty and also with remmina, using the same correct address , but not on the terminal. What I am doing wrong? 

Any help will be high appreciated
Thanks in advance

João

---

### Post by dannyboy79 on 2013-01-18
did you change the real IP? it wouldn't matter if you showed it as those are internal private IP's and no one can do anything with them.

you should be entering
```
ssh username@192.168.0.3
```
or whatever the IP of the server is, it shouldn't have to resolve it's hostname as it's the IP.

---

### Post by steeldriver on 2013-01-18
It's hard to see since you are replacing everything with x's (there really is no need to hide a private LAN IP like 192.168.xxx.xxx) but it looks like you have too many fields - are you trying to append a specific port? e.g. 

```
$ ssh 192.168.1.102:22
ssh: Could not resolve hostname 192.168.1.102:22: Name or service not known
```If so try using the -p option instead e.g.

```
$ ssh -p 22 steeldriver@192.168.1.102
```

---

### Post by Joao Lacerda on 2013-01-18
Thank you friend.

That have worked.

$ ssh -p 22 steeldriver@192.168.1.102

many thanks.

---

### Post by dannyboy79 on 2013-01-18
u don't need to specify the port if your ssh server is listening on the default port, which is 22.

---

### Post by CaptainMark on 2013-01-18
And changing the port is not a huge issue unless you intend on forwarding the ssh connection outside of your lan

---

### Post by Joao Lacerda on 2013-01-18
Beautiful blog!! Very interesting.

---

### Post by dannyboy79 on 2013-01-18
> **Joao Lacerda said:**
> Beautiful blog!! Very interesting.
thanks if you're talking about my blog. ;)

---

### Post by twlkyao on 2013-11-03
I am now facing the same problem, and even worse, I can ssh the server in the lan, but I can't ssh my server form the internet, my iptables is set as  xxx.xxx.xxx.130:20022  to  192.168.0.200:22, but when I do this" ssh [email]server@xxx.xxx.xxx[/email].130:20022, it results the same error, but when I ssh the gateway, I can ssh the server through the lan IP, but not the internet IP, thanks for your reply in advance. My e-mail: [email]qishiyao2008@126.com[/email]

---

