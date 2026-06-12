---
title: "block ping response iptables"
date: 2008-07-09
forum: General Help
---

### Post by dapim on 2008-07-09
i wanna put a rule in my iptables , when somebody ping my adress, for not respond to it

---

### Post by Ramses de Norre on 2008-07-09
iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP

---

### Post by dapim on 2008-07-09
how to configurate for iptables not to responde to ping,so if a try to ping my computer from another machine to don't show nothing in the reply?

---

### Post by Ramses de Norre on 2008-07-09
Well, didn't I tell you how? That command tells iptables to drop every incomming echo request so no answer will be send.

---

### Post by wdaniels on 2008-07-09
> **dapim said:**
> how to configurate for iptables not to responde to ping,so if a try to ping my computer from another machine to don't show nothing in the reply?

A correct reply has already been given by Ramses de Norre:

> **Ramses de Norre said:**
> iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP

However, you do need to run this command with sudo:

```
sudo iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP
```

But if that is the reason you ignored the reply and just repeated your question, you could have at least acknowledged it and explained why you didn't think it resolved your issue.

---

### Post by zurek22 on 2010-01-19
how would you reverse this? if needed

---

### Post by ivboy on 2010-01-22
Hi 

I just installed backtrack 4 in VMware, i used backtrack 2,3 and pre final 4, ubuntu almost all versions and i have never had this problem ... after installing and configure networking ( in VMware the connection is Bridge ) and in backtrack the eth0 interface is geting ip address from the dhcp. The local ping from the shell is ok ... i can ping and the ping has reply ... but if i ping [www.google.com](www.google.com) im getting no reply. But if i try to open google.com with firefox the page opens ...  does anyone knows any solution for this ? I know that this is for ubuntu forum but one of my friend have ubuntu and he have the same problem ... pls any solution ... tnx in advance !

---

### Post by ivboy on 2010-01-23
Tnx again

So i found the solution and i would like to share with all off you ...
The problem was with the NOD32 SS firewal, in the machine that was running the VMware ... when i disabled it, i was getting the reply in shell that i needed. it was a little bit strange but that's it ... :)

Tnx again for the post ...

---

