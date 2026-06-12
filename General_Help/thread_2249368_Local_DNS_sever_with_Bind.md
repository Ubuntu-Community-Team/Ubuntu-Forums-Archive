---
title: "Local DNS sever with Bind"
date: 2014-10-21
forum: General Help
---

### Post by israel7 on 2014-10-21
Hello, i have a problem, in my university we have DNS problems, so i want create a local dns sever, not too large , only that stored some common URL, i think use a chached dnd server with bind, so it stores commons url typed, but i have some problems with that, i first tried working without forward, but it didn't resolve URL, so i add forward, and it work meantime forward is configured but if i tried it, do request and then remove it again, it didn't work again.
Also i need request URL be permanent not temporaly. There is a way that i can do that? i used ubuntu 14.04,and problem is that when i use dig or nslookup it said it can't resolve name. Thz

---

### Post by SeijiSensei on 2014-10-21
Have you tried simply using an off-campus DNS server?  Google maintains two, at 8.8.8.8 and 8.8.4.4.

Edit (as root) the file /etc/resolvconf/resolv.conf.d/head and add these two lines:
```

nameserver 8.8.8.8
nameserver 8.8.4.4

```
Reboot and see if that fixes the problem.

---

### Post by israel7 on 2014-10-21
Hello, thz for your answer, yep i did already try it, my university have a firewall and external dns didn't work, the only one i can use is the one than university provide, but it have some problem about 2 last weeks, thz

---

### Post by MrSteve on 2014-10-21
have you had a look at or tried dnsmasq 
[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3377351/In-a-DNS-bind-Get-Out-With-dnsmasq.htm)

dnsmasq howto
[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

it is available in the repro's ...

---

### Post by SeijiSensei on 2014-10-21
When you mean it "doesn't work," do you mean that they don't resolve addresses for certain sites they wish to block?  If so, we're not allowed to help with that here.  From the [Forum Rules]("http://ubuntuforums.org/misc.php?do=showrules"):
> We do not support circumventing TOS, EULA, etc here. 

---

### Post by Irihapeti on 2014-10-21
Agreed. This appears to be about bypassing the university restrictions, and we don't support that here.

Thread closed.

---

